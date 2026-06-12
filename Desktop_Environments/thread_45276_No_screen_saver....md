---
title: "No screen saver..."
date: 2005-06-29
forum: Desktop Environments
---

### Post by IchBin on 2005-06-29
[COLOR=DarkOrange][FONT=Tahoma]For some reason my screen saver/s will not come on at the set time limit. I have it set for 10 minutes. I cannot get any screen savers to come on at that time limit. I even tried other time limits.  I can preview ALL the screen savers just fine. Is there something I can check or do to make this happen?[/FONT][/COLOR]

---

### Post by oliwally on 2005-06-30
Ok, I'm no linux guru in any sense, but I've had some trouble with my screensaver too. My problem was there the Screensavers were not listed in the screensaver menu.

I've found a solution to the problem after poking around a bit in the forums. Perhaps it will solve your problem too ?

I seems that KDE self-generates a file when you make changes to K Menu. This file is applications-kmenuedit.menu found (on my computer) in ~/.config/menus/. Do a search for it and you will find it in your user folders. Deleting this particular file solved all my problems ! But try it first before deleting. You can do this by creating a temporary folder and moving the file to it, then replacing it if you have no success. 

Would be interesting to see if it works. Let us know !

---

### Post by IchBin on 2005-06-30
[QUOTE=oliwally]Ok, I'm no linux guru in any sense, but I've had some trouble with my screensaver too. My problem was there the Screensavers were not listed in the screensaver menu.

I've found a solution to the problem after poking around a bit in the forums. Perhaps it will solve your problem too ?

I seems that KDE self-generates a file when you make changes to K Menu. This file is applications-kmenuedit.menu found (on my computer) in ~/.config/menus/. Do a search for it and you will find it in your user folders. Deleting this particular file solved all my problems ! But try it first before deleting. You can do this by creating a temporary folder and moving the file to it, then replacing it if you have no success. 

Would be interesting to see if it works. Let us know ![/QUOTE]
 Well I had to install the build-essential and the kernel-headers yesterday for my wireless. After doing that it seems to work. Sorry I was able to try your method. Thanks for posting!

---

