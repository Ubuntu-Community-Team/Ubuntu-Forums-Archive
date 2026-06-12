---
title: "[SOLVED] Notification Area (and other panel add-ons) Error"
date: 2005-12-10
forum: Desktop Environments
---

### Post by antiemptyv on 2005-12-10
So I was going to move my notification area from my top panel to my bottom panel, so I removed it from the top one.  When I went to add it to the bottom panel, a window pops up and says 

> **The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet".**

Do you want to delete the applet from your configuration?

[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][Yes]    [No][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]


So then I tried to add some other things to my panel that I don't already have.  Some of them work, but most don't and return the same sort of error.

How can I get this error to let me add cool thingies to my panels?  Thanks.

---

### Post by arnieboy on 2005-12-10
[QUOTE=antiemptyv]So I was going to move my notification area from my top panel to my bottom panel, so I removed it from the top one.  When I went to add it to the bottom panel, a window pops up and says 



So then I tried to add some other things to my panel that I don't already have.  Some of them work, but most don't and return the same sort of error.

How can I get this error to let me add cool thingies to my panels?  Thanks.[/QUOTE]
try creating a new panel and then delete this panel where uare getting all the errors and then add all ur stuff to the new panel.

---

### Post by antiemptyv on 2005-12-10
Ahh, nope.  The errors occur when working with both current panels and on any new panels I create.  Some of the applets work, though, such as the clock, battery, network connection monitor, volume, view desktop button, and workspace switcher to name a few.  Ones that cause the error are ones such as these:  sticky notes, rhythmbox-applet, weather, system monitor, and (now) notification area since I removed it.  Maybe I should have left well-enough alone...

---

### Post by antiemptyv on 2005-12-11
I got it working by removing and (re)installing gnome-applet and gnome-applet-data via apt-get and then a reboot.  now, ubuntu is up from a 99.8%  to a 99.9% again.

---

### Post by movil on 2005-12-27
[QUOTE=antiemptyv]I got it working by removing and (re)installing gnome-applet and gnome-applet-data via apt-get and then a reboot.  now, ubuntu is up from a 99.8%  to a 99.9% again.[/QUOTE]

I've to add something there, I had the same problem but also problems with python.
The solution was to re-install python 2.4, then the gnome-applets went just fine :)

---

### Post by rooijan on 2006-02-22
After reading this thread I checked and for some reason I did not have gnome-applets installed.  So I installed it and now I have a volume control and wastebasket again.

---

### Post by Rough on 2008-02-16
My panel suddenly developed this problem for no apparent reason.  Reinstalling Python 2.4 fixed it.  Weird.

---

