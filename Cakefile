fs = require 'fs'
cp = require 'child_process'

task 'build', ->

    source   = (fs.readFileSync 'source/github-repos.js').toString()
    template = (fs.readFileSync 'source/template.html').toString()

    template = template
        .replace(/[\r\n]+/g, '\\n')
        .replace(/"/g, '\\"')

    output = source.replace '{{template}}', template

    fs.writeFileSync 'github-repos.js', output
    cp.exec 'uglifyjs github-repos.js >> github-repos.min.js'
