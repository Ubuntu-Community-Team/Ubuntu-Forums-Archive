---
title: "Running AVG causes system halt"
date: 2009-05-30
forum: General Help
---

### Post by Richardcavell on 2009-05-30
Hi everyone,

I'm running Ubuntu 9.04 64-bit on a Macbook2,1.  1 Gig RAM, plenty of hard disk space.  Dual booting with OS X.

I'm running AVG anti-virus from the command-line.  The virus definitions are up-to-date.

 $ avgscan /

If I do this, sooner or later my computer will suddenly stop and go completely black - no shutdown sequence, no screen of death, all fans and hard disks spin down immediately - and I have to reboot.

In order to capture any error messages, I tried:

 $ avgscan / > $HOME/Desktop/scan.log

but all it shows is that AVG exited normally right before the shutdown.  (It does flag a SCSI kernel extension as a false-positive, but that doesn't appear to be necessary for the halt to occur, since I can scan other directories that contain no false-positives and AVG will still crash some of the time).

What's going on?  I realise it could be AVG's fault, but Ubuntu should gracefully shut it down if it doesn't play nicely.

By the way, I recently ran while true; do /bin/true; done in three Terminal windows to send my CPU usage up to 100% for an hour, thereby making my CPU heat up, to see if it was an overheating problem.  That wasn't the problem, it turns out.  However, could it be that AVG is accessing my hard disk so rapidly?

Richard

---

### Post by jrusso2 on 2009-05-30
I think you should run avgscan as sudo if you going to do / or it won't have permissions.

---

### Post by Richardcavell on 2009-05-30
Yes, I run it as root.  If I don't, it will simply skip certain files and print them to stdout with 'Permission denied'.  It's not lack of permission to access files that results in the system halt.

Richard

---

### Post by grungedoobie on 2009-05-30
I can't even imagine what your working with to have to run a virus scanner on your root system files, but wouldn't it be better to scan your drive from an outside source?

Like clamtk from a live cd?

This has worked beautifully for me when taking viruses off of Windows machines.

Just boot up a live cd, install clamtk to ram and scan the desired drive as root.  From what I've seen, clam has most if not all of the up-to-date virus definitions.

In fact, I used clamtk on an ancient laptop from 1996-98 with XUbuntu yesterday to remove a virus from a friends 4G USB thumb drive that Windows Vista wouldn't touch.

Luck to you,

The Grunge

---

### Post by Wiebelhaus on 2009-05-30
You know I've had one heck of a time with AVG for Unix , Horrible time.

Which is why I now use the best Unix offering there is:

[Bitdefender for Unices]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html")

---

