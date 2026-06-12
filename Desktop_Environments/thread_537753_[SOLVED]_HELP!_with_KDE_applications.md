---
title: "[SOLVED] HELP! with KDE applications"
date: 2007-08-29
forum: Desktop Environments
---

### Post by nuir on 2007-08-29
Hi, I use Ubuntu Feisty (with Gnome), I have it installed both in my desktop and laptop. 

Recently I noticed that some KDE applications, like KOrganizer, don't show any menu items, instead I can only see some small hole-like dots. No functionality is lost, I get no errors, and the text elements in the menus are fine, even if I hover the mouse over the empty dots, I can see the tooltips.

This only happens in my laptop, the desktop PC runs these same applications flawlessly.

My guess is that my laptop is missing some libraries, but I have no idea which ones.

I've checked for KDE and QT3 related libraries, but as far as I've compared both machines, it seems both computers have the same libraries installed, so I'm lost here...

Thanx in advance!

---

### Post by kellemes on 2007-08-29
Can you run those applications having this issue from the terminal please?
The output may be interesting.

---

### Post by nuir on 2007-08-30
if I run some of these apps I get something like this:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

but I get it in both computers... so I don't know if it is related to the bug or something else.
I also tried to install all the libraries I have in the desktop into the laptop, but the problem wasn't solved... I'll try next to check some keys using the conf editor, but that could take too long. 

Is there a way to export all the values from conf editor and use them in another computer? like libraries and packages in synaptic?

---

### Post by sumguy231 on 2007-08-30
Just to make sure you don't lead yourself down the wrong path, that error is harmless and unrelated to your problem.

---

### Post by nuir on 2007-08-30
I thought so... thnx!

I also just found out, that if I run these apps from a terminal using *gksudo* they run without problems... I just don't know why they run fine from the GUI in my desktop but not from my laptop... maybe I changed some configs related to *gksudo* or something, I've done so many tweaks that I can't really tell.

---

### Post by FuturePilot on 2007-08-30
> **nuir said:**
> if I run some of these apps I get something like this:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

but I get it in both computers... so I don't know if it is related to the bug or something else.

If you want to get rid of those see this post
[http://ubuntuforums.org/showpost.php?p=3275215&postcount=5]("http://ubuntuforums.org/showpost.php?p=3275215&postcount=5")

---

### Post by Happy_Man on 2007-08-30
Do you just have those apps installed or the entire KDE? That can affect stuff.

---

### Post by nuir on 2007-08-30
I just have those apps, I used to have kubuntu desktop installed in both computers, but now I only have ubuntu.  For this matter, I have installed in both computers the same desktop environment and apps and practically they have the same libraries.

But I have quite different security configurations in my desktop and in my laptop (I'm very paranoid with the latter), maybe I just messed up something... I'll keep looking, and thanks to all of you for your suggestions!

---

### Post by nuir on 2007-09-04
This is getting even stranger...  I noticed that if I change the language localization of Ubuntu in my desktop PC, the one that works fine, these apps do not get updated to the new localization... but in my laptop they change normally and still do weird things with the icons. (So it's not a problem of not being translated yet...)

Does anyone know how or why this happens? It seems though that this localization bug doesn't affect only these apps but others too, so I wouldn't know if these two problems are related.

:confused:

---

### Post by nuir on 2007-09-05
Well... I just solved my problem without even trying to!

A friend of mine asked me to show him the KDE desktop, so I re-installed it, and to my surprise the applications showed wrong (missing icons) even in KDE. So I went to KControl and checked for some clues there. 

It seems that the last time I used KDE, I put some icon theme that left the KDE icons broken even after uninstalling kubuntu-desktop... so I just changed the icons to some others that were not broken, and that was it!

Even after uninstalling KDE again, my apps now show without any problems in Gnome...  I guess there are some configuration files left in the HDD that I didn't know of.

:KS

Thanks to everyone for the help and suggestions!

---

### Post by jzinho on 2007-09-18
Thanks for the hints, guys!

I had the same problem of missing icons in menubars of several KDE programmes, that occurred both in Gnome and KDE. I run the 6.06 Dapper, mostly with Gnome, everything up-to-date. When the solution was not explained clearly, I try to clarify it here for those in need.

Someone has preselected the icon theme "Smokey-Red" to be used in all programmes as a default. For reasons that I don't know it works with some programmes, but only smokes faintly with some others (including Konqueror).

********************************
To make a better selection, go to:
  Settings - Control Center - Appearance & Themes - Icons
  change "Theme" to something else, and see what happens
********************************

I chose the Ubuntu default theme "Human" (which is not the default theme!), and now everything seems to be fine.

Whatever is wrong with Smokey - and possibly with some other themes, too, should be examined thoroughly, and corrected. Please, someone, inform the right Theme Team to rectify the wrong doings. I'm too inexperienced to find the right team in this Ubuntu Forums' mess.

---

