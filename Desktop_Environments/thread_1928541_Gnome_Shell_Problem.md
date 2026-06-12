---
title: "Gnome Shell Problem"
date: 2012-02-20
forum: Desktop Environments
---

### Post by osarusan on 2012-02-20
Background: Ubuntu 11.10 x64, ATI Radeon HD 4775 using catalyst 12.1 drivers (fglrx). I am also using the Gnome shell repository and Gnome 3.2 updates repository.

For a while I had gnome-shell working... Now it won't load. I'm not sure what the problem is.

I can run the Unity desktop fine, but when I log into Gnome, I get no shell, no compositing it seems, and nothing but the desktop wallpaper and the mouse. I can use Synapse to open a terminal. I typed gnome-shell --replace and got the following error:


osarusan@GLaDOS:~$ gnome-shell --replace
Window manager warning: Log level 128: Read-only property 'read-only-view' on class 'GeeAbstractSet' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeSet' of the property on the interface 'GeeSet'

    JS ERROR: !!!   Exception was: Error: extension already loaded
    JS ERROR: !!!     lineNumber = '254'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/extensionSystem.js"'
    JS ERROR: !!!     stack = '"loadExtension([object _private_unknown_GLocalFile],2,true)@/usr/share/gnome-shell/js/ui/extensionSystem.js:254
("systemMonitor@gnome-shell-extensions.gcampax.github.com",[object _private_unknown_GLocalFile],2)@/usr/share/gnome-shell/js/ui/extensionSystem.js:386
scanExtensionsInDirectory((function (uuid, dir, type) {var enabled = enabledExtensions.indexOf(uuid) != -1;loadExtension(dir, type, enabled);}),[object _private_unknown_GLocalFile],2)@/usr/share/gnome-shell/js/misc/extensionUtils.js:180
scanExtensions((function (uuid, dir, type) {var enabled = enabledExtensions.indexOf(uuid) != -1;loadExtension(dir, type, enabled);}))@/usr/share/gnome-shell/js/misc/extensionUtils.js:193
loadExtensions()@/usr/share/gnome-shell/js/ui/extensionSystem.js:384
_initUserSession()@/usr/share/gnome-shell/js/ui/main.js:133
start()@/usr/share/gnome-shell/js/ui/main.js:223
@<main>:1
"'
    JS ERROR: !!!     message = '"extension already loaded"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: extension already loaded
gnome-shell-calendar-server[19622]: Got HUP on stdin - exiting


I have no idea what this means... but does anyone know how to get Gnome Shell working again? (Removing the 2 repos is not an option for me, because to get GIMP 2.7.5 working with my tablet and my processor I need both of those repos enabled... so if that's the only solution than I am SOL I guess... but I'd like to know anyway)

---

### Post by youoh on 2012-02-20
there are old extensions in your system
i fixed it by:

uninstall gnome-shell
clear:
/usr/share/gnome-shell/extensions
~/local/share/gnome-shell/extensions
reinstall gnome-shell

if above gnome-shell 3.2 only install extensions from here:
[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by osarusan on 2012-02-20
Wow... that worked! Thank you sir!

---

