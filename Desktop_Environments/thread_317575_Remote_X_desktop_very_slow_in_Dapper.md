---
title: "Remote X desktop very slow in Dapper"
date: 2006-12-12
forum: Desktop Environments
---

### Post by tlowery on 2006-12-12
I'm running Dapper desktop on a dual-core Dell system.  I use Cygwin on a Windows XP Pro system to connect to my Dapper system via remote X desktop.  Everything was working fine (very responsive during remote desktop sessions) until just recently.  Now my remote X desktop sessions have become very slow.  That is, on the remote desktop application windows are slow to update, painting the desktop background is slow, menu pop-ups are slow, moving windows around is slow, etc.  The only thing I can think of that changed recently is I have been installing software updates when the Ubuntu system notifies me that they are available.  I've tried updating all of my Cygwin packages on the remote Windows XP system, but this did not improve the situation.

Has anyone else seen this problem after recent updates?  Does anyone have any suggestions as to what might be going on here and how to correct it?

Thanks very much in advance for any assistance.

Tim

---

### Post by brownjava on 2007-02-01
I'm experiencing this as well.

Mine is a fresh Dapper PPC install on my old 12" iBook.  I turn on remote desktop and can connect from my Macbook Pro (running OS X) using Chicken of the VNC...but it's unusably slow.

I've even tried setting my VNC client to use 265 colors.  Even that doesn't work.  It's still really slow.

Anyone have any ideas?

---

### Post by invisage01 on 2007-12-12
This is still an issue for me running Gutsy. 

Anyone got any solutions for this one?

cheers

---

### Post by SadaraX on 2008-01-30
I just found a solution to this problem for myself.

I run the tightvncserver for my VNC server. This works well. I limit the colors to 16 bit.

In the past years, I have used xtightvncviewer (and vncviewer). It worked good few a years. 

But about a year ago, xtightvncviewer became slow, slow, slow, SSSSLLLLOOOOOOOWWW......

Well, today I decided to try using KDE's vnc viewer called 'krfc'. I installed it, and configured the VNC settings to be as low as possible.

When I connected to my VNC, it suddenly was just as speedy as before. I can only assume the error is some bug in xtightvncviewer.

---

