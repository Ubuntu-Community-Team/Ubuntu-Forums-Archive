---
title: "Why does accessing my other internal hard drive kill Ubuntu on that drive?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Vcount on 2006-08-28
This actually happened to me before, but I didn't KNOW that looking at one internal hard drive from another is what caused it.  

I have a desktop machine with two internal hard drives.  First, I had Dapper 64 on one, and Dapper 32 on another.  I followed the tutorial here;

[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

to access the data on the 64 bit drive from the 32 bit drive, and right after doing so, anytime I tried to boot 64 bit Ubuntu, it would tell me that I had "stale NFS locks" and no settings could load, and it wouldn't load gnome or anything that would usefully allow me to navigate.  Essentially, from that point it was useless.  

I posted here about what could cause that to happen, and basically got "Who knows?  But your system is borked and needs a fresh install".  

So a few weeks later here, I get around to it.  This time I installed 32 bit Kubuntu on the drive that formerly had 64 bit Ubuntu, but did the same [tutorial](http://www.psychocats.net/ubuntu/mountlinux.html) to access the Ubuntu drive from the Kubuntu drive, and now my main, important, Ubuntu 32 drive is useless.  

I get the same "could not load settings" and "stale NFS locks" messages, no Gnome loads, and it's basically useless now.  Since that tutorial is the last thing I did, I know that's what caused it both times now.  

So my question is, why does this happen?  And more importantly, how do I undo the sharing of drives or otherwise fix my important main drive booting regular Ubuntu 32?

---

### Post by Jose Catre-Vandis on 2006-09-07
Are you seeking to read / write to the second OS (either way?) This could be causing locks.

Please list your respective fstab contents so we can see how you have mounted the respective drives to each other.

Have you tried manually mounting after being fully booted up either using a command line or script. This should help to overcome any possible boot up anomalies that might arise from having D64 on one drive and D32 on another.

Do you need to access the entire 2nd drive or just the home directories?

In answer to you question, you should be able to boot up using a live cd, mount your offending drive, and edit out the sharing in the fstab

FWIW, I have not had any trouble mounting 2nd drives or second OS (XP or Linux) on a booting system, with the Linux ones being rw.

---

### Post by Vcount on 2006-09-07
Well, I did access stuff on one hard drive from the other.  That being the point of sharing the drives, I thought.  I don't know wether that counts as "read", I didn't try to write anything to it, though.  

The first thing I tried was booting in safe mode and changing the fstabs back.  It was interesting, because safe mode on the borked drive wouldn't "sudo" at all.  I had to chmod and chown the drive before it would let me do anything, so there was something screwy with the permissions.  

Unfortunately, by this time I've reformatted the borked drive and vowed to never try sharing drives ever again, so I can't give you the fstabs of the respective drives any more.

---

