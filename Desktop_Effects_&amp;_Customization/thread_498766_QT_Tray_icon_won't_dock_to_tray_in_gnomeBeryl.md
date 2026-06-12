---
title: "QT Tray icon won't dock to tray in gnome/Beryl"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by hotspoons on 2007-07-11
Here's a picture of what's happening:

[IMG]http://i62.photobucket.com/albums/h94/hotspoons/screenshot3.png[/IMG]

Offending program is circled in red. It is a QT program (not part of KDE main) called [qjoypad]("http://qjoypad.sourceforge.net/"). It hasn't been updated much since 2004 (except for GCC 4 updates), and was in the land of time before compositing destkops. When the PC boots, if the desktop is in Beryl, the icon doesn't go to the tray, and instead floats in a little window. It docks fine in metacity.

 I can't find another program that will suit my needs (joy2key doesn't read my joystick). The sole purpose of this program is to have a cheap, hacked apart Playstation-esque USB digital and analogue (I actually removed everything except the circuit board and two analog sticks) controller in the dash of my car, with the right stick sending up, down, left, and right KB commands, and the left stick sending break and scroll lock commands (that is what I have mapped to spin the desktop cube, where I will have [Enginuity engine logging/tuning software]("http://www.enginuity.org/") on one cube face, some as of yet undecided audio application on another cube face, GPS software like iGuidance under wine or Navit on another cube face, and one to spare). This is going out to a 7" lilliput 800x480 flip-out single din touchscreen, and a keyboard and mouse will not normally be used. I'll post pictures of the installation after it is completed (its in an '07 STi with the[ Tactrix openport ECU logging/flashing cable]("http://www.tactrix.com/product_info.php?products_id=31&osCsid=b2ef77cda728961108aff8ab1a784c26"), which has been supported in Linux since Kernel 2.19).

If anyone has any suggestions for similar programs, or a way to get this one to dock (because it does work very well for my purposes), I would gladly take them. Thank you,

-Rich

---

### Post by hotspoons on 2007-07-11
I forgot to add that this is using Beryl 0.21 (.3 would lock up X intermittently, and I couldn't get compiz-fusion to listen to the settings program, but of course that was a week ago and its been through 10 revisions since then) on Feisty 32 bit, Intel core2 duo on i945GZ/intel graphics.

---

### Post by hotspoons on 2007-07-12
I found an application called 'alltray' that will force this thing into the tray, even if it doesn't want to go. I think this will be fine since I never need to access it, I just need it to run. Thanks!

---

