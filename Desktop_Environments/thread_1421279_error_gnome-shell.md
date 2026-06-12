---
title: "error gnome-shell"
date: 2010-03-04
forum: Desktop Environments
---

### Post by mahsom on 2010-03-04
Hello ... 

I use ubuntu 9.04 and installed gnmome-shell.
when run **gnome-shell --replace** receive this error :

```
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
[mahsom@Lintux:~/gnome-shell/install/bin]$ ./gnome-shell --replace
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
    JS ERROR: !!!   Exception was: TypeError: redeclaration of variable minWidth
    JS ERROR: !!!     lineNumber = '229'
    JS ERROR: !!!     fileName = '/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/panel.js'
    JS ERROR: !!!     stack = '@:0
@/home/mahsom/gnome-shell/install/share/gnome-shell/js/ui/workspace.js:20
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'redeclaration of variable minWidth'
Window manager warning: Log level 32: Execution of main.js threw exception: TypeError: redeclaration of variable minWidth
[mahsom@Lintux:~/gnome-shell/install/bin]$ Cannot register the panel shell: there is already one running.
```

what is this problem ?!

---

### Post by fanum on 2010-03-09
Not sure about the error, but have you considered running gnome-shell from the PPA? Here is instructions:

[http://www.webupd8.org/2009/10/install-docky-and-update-gnome-shell.html](http://www.webupd8.org/2009/10/install-docky-and-update-gnome-shell.html)

---

