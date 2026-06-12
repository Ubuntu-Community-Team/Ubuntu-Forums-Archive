---
title: "gnome isnt working properly"
date: 2012-10-19
forum: Desktop Environments
---

### Post by pajser on 2012-10-19
Gnome panels are not showing up!
I turned on my machine with two keyboards and since then on startup I get no panels and virtual keyboard just pop ups right away.
I can run Gnome classic though!
Very weird bug, i cant google it sucesfully :(

I have 32bit ubuntu 12.4, did a update hoping it would fix it...

---

### Post by jerrrys on 2012-10-19
That is a strange one.  Try reinstalling gnome-fallback

sudo apt-get remove gnome-session-fallback

sudo apt-get install gnome-session-fallback

Are you trying to use compiz?

Or is this gnome shell?

---

### Post by pajser on 2012-10-19
> **jerrrys said:**
> That is a strange one.  Try reinstalling gnome-fallback

sudo apt-get remove gnome-session-fallback

sudo apt-get install gnome-session-fallback

Are you trying to use compiz?

Or is this gnome shell?
Thanks for help!
Reinstalling gnome-fallback didnt help.
I did ps -e | grep compiz and seems that am running compiz, I typed it while i was in gnome cllasic witch works allright (though it still pops a keyboard)

---

### Post by jerrrys on 2012-10-19
Try classic - no effects.

Get panels there?

---

### Post by pajser on 2012-10-19
Iam currently using classic and panels show up, tryd no effects and it works too...

I just tryed to launch gnome shell from terminal while Iam in normal gnome (currently broken one)

I get this (not sure is it whole text need to check that):> 
[SIZE="2"][SIZE="1"](gnome-shell:2990): Clutter-WARNING **: Attempting to remove actor of type 'ShellGenericContainer' from group of class 'StBoxLayout', but the container is not the actor's parent.

(gnome-shell:2990): Clutter-CRITICAL **: clutter_actor_insert_child_at_index: assertion `child->priv->parent == NULL' failed
    JS ERROR: !!!   Exception in callback for signal: enter-event
    JS ERROR: !!!     message = '"this._activeContainer is null"'
    JS ERROR: !!!     lineNumber = '1146'
    JS ERROR: !!!     fileName = '"/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js"'
    JS ERROR: !!!     stack = '"([object Object])@/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js:1146
_emit("enter-event")@/usr/share/gjs-1.0/signals.js:124
()@/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js:1437
()@/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js:918
ApplicationsButton()@/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js:885
enable()@/home/marin/.local/share/gnome-shell/extensions/axemenu@wheezy/extension.js:1623
enableExtension("axemenu@wheezy")@/usr/share/gnome-shell/js/ui/extensionSystem.js:221
loadExtension([object _private_unknown_GLocalFile],2,true)@/usr/share/gnome-shell/js/ui/extensionSystem.js:275
("axemenu@wheezy",[object _private_unknown_GLocalFile],2)@/usr/share/gnome-shell/js/ui/extensionSystem.js:385
scanExtensionsInDirectory((function (uuid, dir, type) {var enabled = enabledExtensions.indexOf(uuid) != -1;loadExtension(dir, type, enabled);}),[object _private_unknown_GLocalFile],2)@/usr/share/gnome-shell/js/misc/extensionUtils.js:180
scanExtensions((function (uuid, dir, type) {var enabled = enabledExtensions.indexOf(uuid) != -1;loadExtension(dir, type, enabled);}))@/usr/share/gnome-shell/js/misc/extensionUtils.js:187
loadExtensions()@/usr/share/gnome-shell/js/ui/extensionSystem.js:383
_initUserSession()@/usr/share/gnome-shell/js/ui/main.js:137
start()@/usr/share/gnome-shell/js/ui/main.js:236
@<main>:1
"'

(gnome-shell:2990): Clutter-WARNING **: Failed to set the markup of the actor 'ClutterText': Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Failed to set the markup of the actor 'ClutterText': Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(gnome-shell:2990): Clutter-WARNING **: Failed to set the markup of the actor 'ClutterText': Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

(gnome-shell:2990): Clutter-WARNING **: Attempting to add actor of type 'StButton' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.
Segmentation fault (core dumped)[/SIZE][/SIZE]



compiz doesnt lunch n startup but it lunches fine from terminal

---

