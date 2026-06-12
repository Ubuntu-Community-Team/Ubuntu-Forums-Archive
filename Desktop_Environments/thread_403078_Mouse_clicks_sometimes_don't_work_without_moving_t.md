---
title: "Mouse clicks sometimes don't work without moving the mouse"
date: 2007-04-06
forum: Desktop Environments
---

### Post by utkjamie on 2007-04-06
I've been having a strange problem in Kubuntu/KDE in which I can click a button or a window, etc. with the mouse but nothing happens until I either move the mouse pointer or click a second time. It appears to be completely random and is as if the first click was never communicated to the software.

---

### Post by kidders on 2007-04-07
Hi there,

Your problem may well be a glitch of some kind, but there are two things worth checking first...

[LIST]
[*]KDE is capable of doing some pretty smart things with mouse clicks, including *not* passing them to applications under certain circumstances (particularly when they're not the active task). Have you been customising mouse click transmission policy?
[*]If you're using a USB or RF mouse, it may be going to sleep.[/LIST]I don't suppose either of these is to blame?

---

### Post by utkjamie on 2007-04-07
My first thought was that maybe it was something I had changed in the KDE mouse settings, so I reset the mouse settings to the default settings (and that cleared up a different weird problem I was having) but this click problem is still there.

You know, I didn't think about it before but the problem might be that I'm using a laptop with a touchpad. I had to make some changes in the /etc/X11/xorg.conf file in order to disable the annoying tap clicks. I didn't have any problems initially after those changes, but I had to reinstall Kubuntu after a crash and may have missed something when I rebuilt the xorg.conf file.

I'll poke around with it and post my results.

Thanks!

---

### Post by kidders on 2007-04-07
Hmm... Sorry I can't be of more decisive help. :-( Touchpad + Linux can be one hell of an annoying combination! If anything else strikes me, I'll post back straight away.

**Edit:** Just as I was posting this, I suddenly wondered about accidental input. Could it be that the minimum interval between your last keystroke and your first touchpad activity is set too high ... or is that a totally dumb suggestion?

---

### Post by utkjamie on 2007-04-08
Not a dumb suggestion at all (I was thinking along the same lines). I think setting my double-click interval was causing another problem I was having (scrolling buttons "sticking").

In looking at my xorg.conf file, though, I think the problem might be that my system is configured for a Synaptics touchpad while I actually have an Alps touchpad. That might be the problem. I'll do some digging and see if I can find the correct config for that and post the results for anyone else having the same problem.

---

