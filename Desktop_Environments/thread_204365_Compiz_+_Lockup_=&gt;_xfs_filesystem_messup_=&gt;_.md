---
title: "Compiz + Lockup =&gt; xfs filesystem messup =&gt; No Bash and Freezing X =&gt; Resolution"
date: 2006-06-26
forum: Desktop Environments
---

### Post by cptnapalm on 2006-06-26
I apologize for the stupid title, but that was the sequence of events earlier this evening.

I was running Xgl and it locked up, as is not uncommon.  I make no complaints as it is not ready for primetime and I knew this when I installed it.  But.

After a hard reboot, when Ubuntu started up, it did no xfs_check, which is something I recalled later on.  GDM started up and everything looked peachy keen.  Until I logged out of Gnome or rather tried to as nothing happened and it looked like another hard lock, but I switched to the console.

Upon switching to the console, I logged in and killed gdm.  It did so, but gave me a strange error about hostname.  I rebooted again and ran xfs_check off the live dvd.  Filesystem problems galore.

Oh God.

So I fix xfs.  And reboot.  No console.  Malfunctioning X.  Please shoot me.  Reboot to Live disc.

I mount the partition and find out that /etc/hostname now reads a long string of @s and /etc/network/interfaces is the same.  I manually redid the files so they, respectively, listed my computer's name and the lo loopback.

Reboot and everything seems to be working okay so far.

I post this in case anyone else has such a problem.  Years ago, I ran Debian and it would automatically do a filesystem check and fix when the machine locked up (normally an X problem there too.)

Shouldn't this hardlocking X problem have been solved by now?  I remember this exact same sort of thing occurring when I first started using Linux nine years ago.  That plenty of time for a solution to have been found to this persistent problem.

Patrick

---

