---
title: "Dual monitors and maximising"
date: 2008-07-19
forum: Desktop Environments
---

### Post by Trollslayer on 2008-07-19
I have tried with Gnome and KDE and using Twinview mode  (nVidia graphics) if I maximise a window it covers both monitors rather than one.
Any suggestions?
Ubuntu 8.04 BTW.

---

### Post by mediajunkie on 2008-07-20
I had same problem, even had the tool bars (top and botom) going over 2 screens. So I assume you are using nvidia x server settings? (applications > system tools > nvidia x server settings

If you do, you have to save configuration to X configuration. 
That probably will cause an error message. (permissions issue to write the xorg.conf.backup file) I fixed that by opening a terminal screen and start nvidia settings from command line as root. 

> sudo nvidia-settings 

do your settings and save to x configuration. the next boot should fix your problem. It did with me. 


I do have one issue with this setting though. if I disconnect the second monitor and boot with Laptop screen only, I only get half a screen. 
For now I manually go into console mode and copy the right "xorg.conf" from a backup to work with one screen and reboot. Fixes it but kind of annoying. because I have to do the same thing and copy the file for dual screen mode if I work with twin view again. If anybody would know a solution for that ,,, happy to know it. 

I"m thinking of a hardware solution with a dongle pulling the sync line to the ground making the laptop believe there is a second screen even when not, but I know that isn't a very elegant solution. a fix in the driver or settings would be sooo much better. :lolflag:

---

### Post by Trollslayer on 2008-07-20
Thanks, that sorts the persistance part.
I configured te desktop to get the menu bar to cover 50% as a temporary mmeasure.
When I find out how to solve maximising to one monitor I'll post here.

---

### Post by Trollslayer on 2008-07-20
Thanks, I restarted the system and the toolbar is on the right hand monitor where I want it and windows maximise to the monitor they are on!
As it's a desktop PC I shouldn't have to worry about disconnected monitors.

---

### Post by mojoman on 2008-07-20
post your xorg.xonf and you'll increase your chances of getting help.

Also, is this happening to all applications or only some? 

Is it when you maximize a window or when you toggle to fullscreen mode?

/mojoman

---

### Post by Trollslayer on 2008-07-20
Err... it's workingn now, sorry if my previous post didn't make that clear.
Thanks.

---

### Post by b.m on 2008-07-22
Trollslayer, could you tell us what you did?

I have the opposite problem. I want my screens to maximize to both monitors instead of just the current one. My test case is World of Warcraft running under Wine. I will have to figure out how to differentiate that from mplayer (I don't want movies to play on 3360x1050 with a division line in the middle), but that is the next step. A x.org restart to alternate between xorg.conf's (for movies/gaming) would be bad, but better than no solution, so I am more worried about getting the maximization on two monitors for now.

thanks!

---

