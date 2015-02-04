    chai = require 'chai'
    chai.should()

    describe 'Databind', ->

      teacup = require 'teacup'
      teacup_databind = require '..'
      teacup.use teacup_databind()

      it 'should process `bind`', ->
        html = teacup.render ->
          {div} = teacup
          div bind: component: 'foo', -> 'hello'
        html.should.equal '<div data-bind="component: foo">hello</div>'

      it 'should process `bind` with multiple values', ->
        html = teacup.render ->
          {div} = teacup
          div
            bind:
              component: 'foo'
              value: 'expect'
          , -> 'hello'
        html.should.equal '<div data-bind="component: foo, value: expect">hello</div>'
