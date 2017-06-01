sublime text 3
===============
my settings and packages 

<a name="key-bindings"></a>
## key bindings 
| key                         | action                                 |
| :--------------------------| :-------------------------------------|
| Ctrl + Shift + P            | command pallete: package install, list |
| Ctrl + P                    | open file, :line-number, @function     |
| Ctrl + R                    | list all functions in file             |
| `Ctrl + M`                  | goto matching brace                    |
| Ctrl + \`                   | Show Console                           |
| `Ctrl + Shift + H`          | HTML Prettify                          |
| Ctrl + Shift + /            | comment code                           |
| Ctrl + K, Ctrl + B          | toggle_side_bar                        |
| Ctrl + Alt + F              | format javascript w/semistandard       |
| `Ctrl + Alt + p`            | switch project                         |
| `Ctrl + M`                  | __matching bracket__                   |
| `Ctrl + Alt + Super + Down` | goto right bracket                     |
| Ctrl + Alt + Super + S      | select text in brackets                |
| Control+K, A                | Show all errors                        |
| Control+K, N                | Show next  errors                      |


<a name="resources"></a>
## resources
- [Sublime-text-3](http://www.sublimetext.com/3)
- [package control](https://packagecontrol.io/)
- https://github.com/jfilter/Sublime-Text-Plugins-for-Frontend-Web-Development
- https://github.com/rballen/sublime-text-3.git

<a name="setup"></a>
## setup
1. cd to Preferences --> Browse Packages and Open in terminal
2. cd into User/
3. init a git repo and assign origin to the github repo
4. fetch from repo and reset local files
5. negate and add to .gitignore whatever you want to keep in sync
6. subsequent visits just run `git pull` or `git push`

```sh 
cd ~/.config/sublime-text-3/Packages/User
git init
git remote add origin https://github.com/rballen/sublime-text-3
git fetch
git reset --hard origin/master
``` 


<a name="user-snippets"></a>
## user snippets 
- Tools > Developer > New Snippet 
- save in Packages/User dir from above with .sublime-snippet file extension.
- possible scope values: text.html, source.js, source.css, text.html.markdown, text.html.markdown.multimarkdown, source.shell

```html
<snippet>
	<content><![CDATA[
		<div class="$1">
			
		</div><!-- /${1/\*//} -->
]]></content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<!-- <tabTrigger>hello</tabTrigger> -->
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
	<!-- <scope>source.python</scope> -->
	<tabTrigger>d</tabTrigger>
	<scope>text.html</scope>
</snippet>
```


<a name="ternjs"></a>
 ternjs 
---------------------------------------

| Plugin      | README                                            |
| ----------- | ------------------------------------------------- |
| `alt+.`     | Jump to the definition                            |
| `alt+,`     | Jump back                                         |
| `alt+space` | on a variable, select all references in that file |
| `alt+o`     | quick documentation                               |


<a name="setup-1"></a>
### setup  
```sh
cd /path/to/sublime-text-N/Packages
git clone git://github.com/ternjs/tern_for_sublime.git
cd tern_for_sublime
npm install 
```
"auto_complete_triggers": [ {"selector": "text.html", "characters": "<"}, {"selector": "source.js", "characters": "."} ]

<a name="settings"></a>
###settings 

libs: browser, chai, ecmascript,jquery, underscore 	

plugins: angular.js, commonjs.js, complete_strings.js, doc_comment.js, es_modules.js,modules.js, node.js, node_resolve.js,require.js, webpack.js 


create  ~/.tern-config
```json 
{
  "plugins": {
    "node": {},
    "es_modules": {}
  },
  "libs": [
    "ecma5",
    "ecma6"
  ],
  "ecmaVersion": 6
}
```

<a name="eslint"></a>
## eslint
this was a confusing mess just like javascript 2018ad or whatever. just copy settings and pray.


eslint --fix myfile.js
semistandard --fix gulpfile.js 

### setup
1. install from Package Control: SublimeLinter, babel
1. view-->Syntax --> Open all with current extension as... --> Babel --> JavaScript (Babel) for .js and .jsx
1. npm install -g semistandard
1. add global packages path to SublimeLinter or add global packages to $PATH
`- sudo ln -s /home/ra/.nvm/versions/node/v6.9.4/bin/semistandard /usr/local/bin`
**or**     
1. which semistandard
	1.. /home/ra/.nvm/versions/node/v6.9.4/bin/semistandard
	1. Tools --> SublimeLinter --> User Settings.
1.  install from Package Control:  SublimeLinter-contrib-semistandard
1. npm install semistandard-format -g
1.  install from Package Control:  StandardFormat	
	1.	Preference --> Package Settings --> Standard Format --> Settings - User
```json
{
	"PATH": [ "/home/ra/.nvm/versions/node/v6.9.4/bin"],
	"commands": [
		["semistandard-format", "--stdin", "--fix"]
	],
	"format_on_save": false,
	    "log_errors": true,
}
```  

- maps `CTRL+ALT+F` to format code
 - restart sublime

1. `cmd+shift+p`  search for 'toggle' then  SublimeLinter: toggle linter 
	1. to make usre semistandard and standard is enabled
1. `npm install --save-dev eslint eslint-config-airbnb-base eslint-plugin-import`
```json
   env: {
        es6: true
    }

{
  "extends": "airbnb-base",
  "plugins": [
    "import"
  ],
  "env": {
     "browser": true,
     "jquery": true
  },
  "root": true,
  "rules": {
    "comma-dangle": ["error", "never"],
    "max-len": 0,
    "no-console": "off",
    "import/newline-after-import": "off",
    "no-unused-vars": 0
  }
}
```
   
