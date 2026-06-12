---
title: "Sudden mouse lag until suspend/reboot"
date: 2010-05-02
forum: Desktop Environments
---

### Post by vek on 2010-05-02
I just had the mouse suddenly lose hardware cursor capability for no apparent reason.  I was just typing in a terminal.  All of a sudden (I only noticed when I stopped typing since I put the mouse down to type) I noticed that the mouse was moving at maybe 1-2fps, no hardware acceleration at all.  Typing also slowed to a crawl.  The rest of the system continued to work fast and snappy as before.  The CPU usage was minimal, system monitor (and TOP) reporting almost zero use.  Web browsing and actual use of the system seemed to be as snappy and responsive as ever, just input was incredibly low as if it was only sampling at about 2hz.

I wasn't applying any system changes or running any new programs at the time, and it was working just moments before.  All I was doing was downloading files, working in a terminal, and listening to banshee play some music.  Its disturbing that something would just break like that mid-sentence basically. :confused:

It went away when I suspended and resumed, but thats a pretty destructive thing to do during downloads.  If this happens again, what should I do instead?  Anyone else had this happen?  Altering mouse preferences, restarting compiz, plugging/unplugging devices, and leaving and re-entering graphics mode (by switching consoles) had no effect.

---

### Post by vek on 2010-05-19
Okay, this is still happening.  About once a day, and almost always when I'm **not** using the mouse, both keyboard and mouse start to lag as if the sample rate has been drastically lowered.  (i.e., I'll walk away for 5 minutes and come back and its all slow).  This is definitely input lag only - videos, games, etc, still run at full framerates (but mouse movements are slow).

The cursor is actually still updating graphically at full speed, but its like the kernel feed of the mouse and keyboard data only updates at a very low rate.  Compiz still runs at full speed, the web still browses at full speed, music plays fine, etc.

Note:  The input lags even in text mode, keyboard input, so its not specifically mouse lag... and the only cure is to reboot, suspend, or hibernate.  Its almost like the mouse/kb go to sleep or something and only half wake up.

XInput mouse events come in at about 5hz instead of the normal 120hz, for example. 

I want to report this as a bug but as usual, I have absolutely no idea where the appropriate bug tracker lies.  "Launchpad" is pretty useless since it has a billion little projects with no real way to find out what causes mouse lag.  It doesn't help that about 8 different subsystems are involved in the input stack (HID?  XOrg?  the xorg input driver?  the KERNEL input driver? it looks like this could be a problem at a very low level... since it happens even in text mode, and affects input on the console from the keyboard...)

Any suggestions where to look next?

---

### Post by jleppers on 2010-06-24
I am having the same issue in Ubuntu server 10.04 with KDE installed, it worked fine for a while then just did the same thing the above posts said. This is a new installation of ubuntu server as well and i did install my graphics driver via Hardware detection tool. My graphics card is an ATI Radeon HD 2400 Pro.

---

### Post by vek on 2010-06-24
I've plugged my mouse and keyboard into a port which isn't shared by the sound card IRQ.  The error still happens, but it no longer kills my mouse also.

If you can, plug your mouse into a different USB port (preferably something far away from the one its currently into) and it should remain unaffected.  For me it meant unplugging it from the monitor, since that hub decided to be on the same IRQ as the sound card...

Not a real fix, but at least something...

---

### Post by refjaf55 on 2010-06-25
i have had the same problem in the past...

---

