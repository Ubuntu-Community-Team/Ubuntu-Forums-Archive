---
title: "Emerald Error"
date: 2008-07-18
forum: Desktop Environments
---

### Post by metoor30 on 2008-07-18
I have used Compiz/Emerald with Edgy and Fiesty.  I just installed Hardy on my new laptop.  I am used to Nvidia and Dell and now I am HP and ATI.  I was able to get Emerald working with the advanced desktop effects working while my laptop is not docked.  When I dock my laptop and configure X for dual monitor using xinerama (or without), I get the following error when I run emerald --replace:

(emerald:9629): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

I have tried to do some research on this and haven't found any helpful information.  It would seem like it is something in the xorg.conf file that I am just missing.  I attached my xorg.conf to this post.

Normally I wouldn't care and just use metacity, but I get some unexpected behavior that I assume is related.  Whenever I lock my system of the screen saver my screens (dual) go black and I cannot get them to respond.  I tried ctrl+alt+f1, ctrl+atl+back and ctrl+alt+del and nothing works.  I have to power down my machine and turn it back on.

The Screensaver preview doesn't work and winecfg completely screws my display and I have to reboot.

I also searched my Xorg log and found this:

Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().

Thanks for any help.  By the way, my system is completely up to date, I have tried to reinstall emerald and have tried Envy and the ATI drivers from the ATI site.

---

