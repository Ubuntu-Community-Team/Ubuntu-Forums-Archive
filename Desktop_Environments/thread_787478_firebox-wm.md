---
title: "firebox-wm"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Harii on 2008-05-08
Has anyone else seen this window manager?
[http://firebox.intuxication.org/?page=0](http://firebox.intuxication.org/?page=0)

looks real nice and lite and has a good review at:
[http://urukrama.wordpress.com/](http://urukrama.wordpress.com/) 

the alt-s dmenu is neat!!

but i'm looking for info on the proper way to configure idesk & wbar with firebox in fbconf(firebox-tool) settings?

I wish there was a Guide out there;)

---

### Post by Harii on 2008-05-18
info at:
[http://antix.freeforums.org/firebox-wm-t630.html](http://antix.freeforums.org/firebox-wm-t630.html) 

I have screenshot here:
[http://www.facebook.com/album.php?aid=2001933&l=56aa3&id=1184812485](http://www.facebook.com/album.php?aid=2001933&l=56aa3&id=1184812485) 

So far only one screenshot yet of firebox--the rest are of blackbox.

I still need to know the proper way to tune the wbar and conky to the desktop--using the fbconf tool.

---

### Post by urukrama on 2008-05-22
Don't idesk, conky and wbar work under Firebox as under any window manager?

You shouldn't need fbconf for this (since that only governs firebox itself).

As for the guide, most of the non-wm specific settings (Gtk themes, icons, wallpapers, idesk, panels, etc.) are covered in my Openbox guide. Firebox is still very young and still fairly basic in configuration -- everything you need to know to work with it can be found in the [Firebox documentation]("http://firebox.intuxication.org/?page=2").

EDIT: judging from [this screenshot]("http://www.facebook.com/photo.php?pid=30074263&id=1184812485&l=56aa3") you did get wbar and conky running. Are they not working properly?

---

### Post by Harii on 2008-05-23
-yes--your guide is very good (thank you) and your bog is how i found this great WM (again thanks).

-yes--you should always check the Doc's first, google and then ask for help last. ---some would say newbies should not use a minimal window manager.

---OK---
yes-n-no! yes it works with themes default wallpaper but not after you change the wallpaper using the fbconf tool. You get a box of the login screen--no matter how long you sleep wbar.

I'm trying to use theme wallpaper for each (v)desktop.
Earth,wind,fire and water theme wallpaper--that part will work but the wbar problem.
The solution i came up with are:
-not useing wbar
-change the wallpaper link in the theme
-use a toggle
>  
# Filename:      wbartoggle.sh
# Purpose:       toggle wbar on/off from menu
# Authors:       Kerry and anticapitalista for antiX
# Latest change: Sun April 13, 2008.
################################################################################

#!/bin/sh

if pidof wbar | grep [0-9] > /dev/null
then
 killall wbar 
else
 wbar -j 0.0 -p top -z 1.8 -above-desk
 fi
 
i know that firebox is very young and Cyrille Bagard has done a great job.

---

### Post by kerry_s on 2008-05-23
i'm a little lost, what exactly do you need help on?

conky, you would configure with a text editor.
wbar, i cant remember, but i think that was by text editor as well.

:confused:

---

### Post by Harii on 2008-05-24
I switch to tablaunch and i don't have the wallpaper problem.
Because of the auto-hide.

There is more than one way to skin a cat.

Disclaimer:)

Firebox is not recommended for anyone needing a stable system or anyone who is not comfortable running into occasional, even frequent breakage. Firebox could possibly make your computer go Crash! Therefore Firebox comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.--Don't drink and drive--

But it that happens less often than micro-crap!!

I use firebox 98% of the time now--crash only once--my fault
Screenshots link:[http://www.facebook.com/album.php?aid=2001933&l=56aa3&id=1184812485](http://www.facebook.com/album.php?aid=2001933&l=56aa3&id=1184812485)
Thank you guys for responding--

---

