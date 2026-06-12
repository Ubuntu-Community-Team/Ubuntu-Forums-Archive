---
title: "Why I Can't Use Ubuntu"
date: 2005-12-08
forum: General Help
---

### Post by liminal on 2005-12-08
There are many reasons why I'd like to be using Ubuntu, but there are two issues that keep me from using it. I thought it might be constructive to post them here:

1. Hibernate doesn't work. Pressing the 'sleep' key on the keyboard does nothing. Choosing hibernate from the shutdown menu does nothing. I saw a presentation from an ubuntu person who bragged about how many laptops they tested for this release, but this is a desktop and it just doesn't work. This is crucial to me using ubuntu because of the time it takes to start the computer from off. I'd rather use MSWindows and have a near-instant on from sleep, than have to wait for startup memory tests, etc. and still not have my last session state preserved.

2. The screen flickers at high resolutions. I posted about this when I installed 5.04 but didn't find a solution. I'd hoped it would be fixed with 5.10, but no. The installation detected everything perfectly right down to the brand names. But I get flickering horizontal lines that make using the OS an uncomfortable experience.

So those are my complaints. If anyone knows a solution, that would be great, but they seem like issues that will have to wait until a later release. So until then, I'll be waiting too.

---

### Post by aclaunch on 2005-12-08
No answers but some comments: why are you hibernating you box? I just leave mine on all the time with a screensaver. 

As for the flicker, you may need to change your refresh rate settings in /etc/X11/xorg.conf. Look at that file with "less /etc/X11/xorg.conf" and check the monitor settings. Compare this to the settings posted by the monitor manufacturer. If you want/need to change anything either use "sudo dpkg --reconfigure xorg-xserver" or just edit /etc/X11/xorg.conf directly and restart X.

Good Luck,
Alan

---

### Post by Roobert on 2005-12-08
[QUOTE=aclaunch]No answers but some comments: why are you hibernating you box? I just leave mine on all the time with a screensaver.[/QUOTE]

Or, if he/she needs to secure the computer in their absence, just lock screen. Same effect as hibernate, and password-protected too.

---

### Post by canadianwriterman on 2005-12-08
Have you tried going into **Preferences > Keyboard Shortcuts **and reprogramming the "Sleep" function to your sleep key? Just highlight the sleep entry on the left side of the list, then hit the sleep key on your machine. Perhaps you've already tried this.

---

### Post by liminal on 2005-12-08
I hibernate because the computer (fan) is loud and is in my living space.

Hibernating from the shutdown menu has no effect, so remapping that function to another key will not help.

---

### Post by Robocoastie on 2005-12-08
isn't it actually the 3d drivers that keep power management from working properly? Which means this isn't an "ubuntu" issue but a problem Linux-wide.

---

