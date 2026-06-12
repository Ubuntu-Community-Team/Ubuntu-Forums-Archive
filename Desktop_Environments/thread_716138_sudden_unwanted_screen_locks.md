---
title: "sudden unwanted screen locks"
date: 2008-03-05
forum: Desktop Environments
---

### Post by kc600 on 2008-03-05
Gdm locks screen at unexpected moments: I get kicked back into the login screen.
Other active session are not affected.
When i log in again, all my applications are still open.

This happens sometimes when i am actually doing something, 
sometimes when the machine is idle.

Some platform info:
Ubuntu 7.10 (Gutsy Gibbon) with kernel 2.6.22-14-generic
The box is an HP Pavillion a6310 with an ATI Radeon HD2350 graphics card 
which shows up as follows in lspci:
04:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c7
I installed the radeonhd driver instead of the default. 

Does anyone recognize this problem?

---

### Post by inozemtsev on 2008-03-05
I'm getting something like this too. I have disabled screen locking on my machine. However, every now and then the screen fades to black, as if the screensaver is starting. This is when I am actively using the computer! This is extremely annoying.

I think I have an idea about what is happening. I have my computer set up with separate screens in xorg, no xinerama. So, if I've been using one screen for a while, gnome thinks I'm idle (on the other screen) and starts the screensaver (which blanks both screens). Anyone know if this is what's happening, and if I can fix this without disabling the screensaver entirely?

---

### Post by inozemtsev on 2008-03-05
Yes, this seems to be the cause of the problem. Someone's already reported this: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/87317](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/87317)

---

### Post by kc600 on 2008-05-18
I upgraded to hardy now and the problem is gone.

edit: Well, I have another one now... [http://ubuntuforums.org/showthread.php?t=809071](http://ubuntuforums.org/showthread.php?t=809071)

---

