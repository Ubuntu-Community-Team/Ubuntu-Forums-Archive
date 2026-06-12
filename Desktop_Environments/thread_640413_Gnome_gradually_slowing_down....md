---
title: "Gnome gradually slowing down..."
date: 2007-12-14
forum: Desktop Environments
---

### Post by njparton on 2007-12-14
Having installed gutsy x64 about 2 weeks ago, I'm starting to experience dramatic slowdowns in how fast gnome loads after logging in. My hardware is in my sig below and I'm using the latest nvidia drivers.

I installed using the reiserfs file system, although I've experienced this with ext3 a few weeks ago before a complete (and unrelated) reinstall. I've implemented the data writeback optimisation.

When I login, the desktop background appears, then 10-20 secs later the desktop icons, followed 30-40 secs later by the menu bars. It can therefore be a good minute plus after login before I can start using anything. There's quite a bit of hard drive thrashing going on.  I've got 2 GB RAM and a 4 GB swap file on a SATA drive. 

If this was Windows I'd defrag the hard drive and run a registry cleaner/optimiser.  

What can I do speed up gnome and/or track what's causing the slowdown? It wasn't this slow when freshly installed.

---

### Post by njparton on 2007-12-15
No-one have any ideas?

---

### Post by Linteg on 2007-12-15
Did this happen after installing some specific app? Do you have a lot of applications starting when logging in? Open System->Preferences->Sessions and deselect those you don't need.

---

### Post by Kulgan on 2007-12-15
I have somewhat of the same condition, just not quite that bad. For me it happened after updating to Gutsy and set emerald and some other things to start with the session. I don't get the background to look at, but the solid brownish-yellow colour that should be present for about two seconds. 
I haven't tried removing anything yet, and I'm not all that fussed, really, so long as it doesn't get any worse...

---

### Post by ubuntu-freak on 2007-12-15
It's Compiz Fusion. Happens to me in Sid. I guess CF isn't polished enough yet. CF and GTK seem to have problems starting together. As some things are still managed by the GTK WM.

---

### Post by njparton on 2007-12-16
I'm not using compiz fusion as I use my ubuntu box as a nas device.

I've decided to try uninstalling all the desktop stuff (ala a server) or to start from fresh with a server install.

I only have openssh and samba installed over and above a normal desktop installation.

---

### Post by njparton on 2007-12-16
Well, you may have been correct.

I've uninstalled all the compiz related packages via synaptic and rebooted. Seems a lot quicker.

However, I can't get any windows to fill the screen now, and the title bar is off the top of the screen and covers the upper gnome bar :(

I'll dive into my X config files to see if there's anything wrong there and try another reboot...

Anyone any ideas how to address this issue?

---

### Post by ubuntu-freak on 2007-12-16
That's very odd. Not heard of that exact problem. Try apt-get purge compiz-core, think that's the command (I'm on my phone). Then reinstall the gnome desktop for good measure.

---

### Post by njparton on 2007-12-17
Thanks for your reply, but the solution below worked for me (in case anyone else stumbles across this thread):

[http://ubuntuforums.org/showthread.php?p=3968240](http://ubuntuforums.org/showthread.php?p=3968240)

---

