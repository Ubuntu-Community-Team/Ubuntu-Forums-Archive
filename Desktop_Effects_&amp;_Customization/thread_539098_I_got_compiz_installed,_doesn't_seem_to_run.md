---
title: "I got compiz installed, doesn't seem to run"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by bbqsauced on 2007-08-30
Ok, so I got Compiz and Emerald installed, and it didn't seem like I ran into any errors.  Anyhow, I go to run them, and I get the following error when trying to run compiz --replace:

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

The screen flickers for a second, and nothing seems to happen.

When I try emerald, I get the following:

(emerald:6231): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

I have an 8800 GTS, (running nvidia drivers) OpenGL is running, and the version of Compiz is 0.5.2.

Any help would be greatly appreciated.

---

### Post by hidden_leaf_sasuke on 2007-08-30
do you have any error during nvidia driver installation?

---

### Post by bbqsauced on 2007-08-31
I had quite a bit of trouble installing the drivers for my 8800 GTS, so there could have been a problem there.  When I run my Nvidia settings and try to save any of the changes to my xorg.conf, I get the following error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Since I get that error, any time I reboot, it always comes up with the default resolution, etc.  Maybe this has something to do with not being able to get Compiz to work?

I checked a bunch of different guides, I tried removing everything then reinstalling it a different way with a script that was in one of these topics.  The script created a Compiz Fusion Icon in my Applications menu, but when I run it, it does nothing.

Also, I read somewhere that I may have to get Xgl running, but I have no idea how to do that or if its even needed.

This has been really frustrating and I'd appreciate it if I could get some help to resolve these issues.

---

