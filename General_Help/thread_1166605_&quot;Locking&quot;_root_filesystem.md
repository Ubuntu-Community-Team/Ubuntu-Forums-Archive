---
title: "&quot;Locking&quot; root filesystem"
date: 2009-05-21
forum: General Help
---

### Post by iscariot on 2009-05-21
Hi,I'm working on a fast-on-fast-off system.  Is it possible to have the entire filesystem read only?

---

### Post by asmoore82 on 2009-05-21
sounds like a bit of paradox -
a cold boot will always be limited by the read speed of the hard drive;
regardless of whether the root FS is read-only or not.

you can set up a system to run from a compressed read-only image like a LiveCD -
that could be quick-on-instant-off, but you would have to be very careful
to unmount any persistent storage before using the instant off.

---

### Post by Oblivion_4 on 2009-05-21
I'm a huge noob but I believe "sudo chmod -R 444 /" will do the trick

---

### Post by dcstar on 2009-05-21
> **iscariot said:**
> Hi,I'm working on a fast-on-fast-off system.  Is it possible to have the entire filesystem read only?

Try making a Hibernate image file R/O.

---

### Post by colau on 2009-05-22
> **dcstar said:**
> Try making a Hibernate image file R/O.
Would you please tell about Hibernate image in detail?

---

### Post by lensman3 on 2009-05-22
Try a remount of the root file system using

"mount -n -o remount,ro /"         Between the quotes. 

I think that /tmp should be read-write or on a ram-disk.  When the OS writes all the running programs stack's to disk, with the root file system as readonly, I don't think it will be able to shut down.  There will be no place it can write to.  


Don't to the "chmod 444" otherwise the binary commands will loose the execute bit and then nothing will run!

You might get one of the all flash disks that have no moving parts.  Those shut down in about 1/2 the time as a regular disk.

---

### Post by iscariot on 2009-05-22
Maybe I should clarify this...

I've got an arcade machine that has an ubuntu machine at it's core.  I've already got it configured to boot when I throw the power switch.  When I turn the system off it cuts power to the entire machine.  I'm trying to avoid the whole issue with it not being properly shut down.

OBTW, is there a way to remove openoffice without removing everything else?  Seems I can't do it without removing ubuntu desktop.

---

### Post by trivialpackets on 2009-05-22
you can remove it safely.  ubuntu-desktop is a metapackage and doesn't break anything to remove to my knowledge.

---

### Post by lykwydchykyn on 2009-05-22
You can have the root partition mount read-only, but I'm pretty sure that causes some things not to work.  A lot of parts of the system need to write out to files to function.

If you're really keen on doing this, and not averse to some hackery, the trick is to figure out what directories need to be writeable and mount them to a ramdrive.

Or the easy way is to use something like remastersys to make a liveCD iso of your installation, then use something like unetbootin to put it on a flash drive.  Then just boot to that.

---

### Post by lykwydchykyn on 2009-05-22
> **Oblivion_4 said:**
> I'm a huge noob but I believe "sudo chmod -R 444 /" will do the trick

This will break your system.  Completely.

Don't do it.

---

### Post by solitaire on 2009-05-22
OK guys think we need to clarify a few things..

You have an arcade style machine running Ubuntu. 
You have it set up to power on when you power it from the mains.
You wish it to be able to shutdown safely when the power is turned off at the mains?
Sounds like you want an embedded version. or a Live CD equivalent

*my idea* (if totally wrong please correct me!)

Only thing I can suggest is to Create your install (with all programs set up the way you want them).
Then turn that into a "liveCD" using something like "remastersys". Then use the "USB Startup Disk Creator" to put the ISO onto a Flashcard.

Then set the Flashcard to be "readonly".

The Arcade will load the Main OS when powered, also if you kill the power the flash drive should not be altered or damaged letting you reboot as normal next time.

---

### Post by iscariot on 2009-05-22
That might work, but I'm booting off of a CF->IDE drive with a HS card there.  I don't think i can lock one of those cards.

---

