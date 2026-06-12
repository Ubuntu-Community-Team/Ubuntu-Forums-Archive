---
title: "rdesktop freezes gnome"
date: 2006-06-16
forum: Desktop Environments
---

### Post by kirsche on 2006-06-16
Hi everybody,

I was just wondering if somebody saw the same behaviour.
I'm using rdesktop to connect to several machines (directly or via tunnel).
At some point, the rdesktop session gets stuck (doesn't matter why) and Gnome freezes for a couple of minutes. I can't click anything or use the keyboard (apart from killing Gnome or switching to the console sessions).

After a while it starts wokring again... It's ust a bit annoying...

Thanks

Marko

---

### Post by scxtt on 2006-06-16
can you try using VNC?  are you connecting to windows boxes?

---

### Post by kirsche on 2006-06-16
I use VNC too - don't see the problem there.
Only with rdesktop - just happend again.
This time through a ssh tunnel - could work in the rdesktop session, but as soon as the pointer left the focus of the rdesktop, I couldn't do anything - had to restart X

---

### Post by chiel on 2006-06-23
I have exactly the same problem. Only happens with RDP, not with VNC. Just leave your RDP session unattended for a few minutes and the whole thing won't respond to mouse movements. I can switch between workspaces fine, but the mouse just won't respond anymore and I also need to restart X to get a responding desktop again. Which is not so nice if you were just editing documents/scripts... If anyone knows how to fix this problem, I would *love* to hear it.

---

### Post by derek_i on 2006-07-01
[QUOTE=chiel]I have exactly the same problem. Only happens with RDP, not with VNC. Just leave your RDP session unattended for a few minutes and the whole thing won't respond to mouse movements. I can switch between workspaces fine, but the mouse just won't respond anymore and I also need to restart X to get a responding desktop again. Which is not so nice if you were just editing documents/scripts... If anyone knows how to fix this problem, I would *love* to hear it.[/QUOTE]

Same problem here. Tried rdesktop 1.4.1 and also compiled 1.3.1 as a test. Both losing mouse events while connected RDP. I have Gentoo clients connecting to the same server using rdesktop 1.3.1 without a problem. This is happening with Breezy and Dapper clients.

Any ideas?

-D

---

### Post by rossellamj on 2006-07-07
I'm having the same exact problem, dapper freezes and I doesn't respond to mouse clicks or anything, I've noticed it happens while I'm using RDP to connect to remote machines. The only thing I can do it restart the gui and re-logon. The last few times it happened I switched to a different terminal and checked the processes with 'top' but everything looks very normal. This happens 3 4 times a day, it's very annoying, does anybody know what causes this?

---

### Post by teomatto on 2006-07-14
i have the same problem with my acer power m5/m6 machine with ati graphic card.

It happen whe i have 2 rdesktop session (with one all is ok)

need help please

---

### Post by akutz on 2006-07-14
Same issue here as well.  It is actually getting to the point of making me want to go back to Windows on my desktop because I cannot abide by me having to kill GDM every time this happens.  Especially since there is no graceful way to shutdown the VMs running in VMware workstation when rdesktop locks up GNOME.

HELP!

---

### Post by thornelawler on 2008-01-14
The problem isn't that rdesktop freezes gnome when it crashes: you can still ctrl-alt-f1, log in and kill the rdesktop process with -9.

The problem is that rdesktop is crashing. I can't get it to run for ore than 30 seconds on end now. I don't have the option of VNC: my employer doesn't let VNC through their firewall, only rdp.

This is the tearing point: rdesktop is the most trivial and completely vital application on my ubuntu PC. Not only does it not work, it doesn't even appear to have a debugging or logging option.

---

### Post by pmorch on 2008-03-09
Just wanted to say that I'm experiencing it too - And it seems there is [a bug for it]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/81854").

---

### Post by luxor on 2008-03-11
I've experienced the same problem, and tracked the problem to redirecting sound to the rdesktop client.  Whenever a sound event is sent to rdesktop, there is a high probability of rdesktop crashing.  Disabling sound solves the crashing issue, but it really is bug that needs to be fixed.

---

### Post by rekster on 2008-07-02
I have an identical problem.  Sometimes if I wait for a few minutes it begings responding again, otherwise I Ctrl-Alt-F1, kill the rdesktop process then restart it again.  This is driving me nuts, is there no progress on this problem?

---

### Post by rekster on 2008-07-04
Do we know if this problem is even being looked at?  Its driving me nuts.  Someone suggested turning off audio redirect which i have done, but it still freezes randomly and intermittently.

---

