---
title: "Trouble mounting/burning PSX CD"
date: 2009-05-06
forum: General Help
---

### Post by Inane_Asylum on 2009-05-06
I installed PCSX and finally got it working great.  The one problem is, I'm getting tired of lag due to the CD having to spin up again.  So I figured I'd use the .iso option.  Basically, Brasero refuses to rip it (it hangs at the first step), Alcohol 120% isn't seeing the CD on my VirtualBox WinXP installation, and I can't seem to mount it to try dd.

This is all I get:
```
cullens@cullens-laptop:~$ dd if=/dev/cdrom of=FFVII.iso
dd: reading `/dev/cdrom': Input/output error
32+0 records in
32+0 records out
16384 bytes (16 kB) copied, 4.0745 s, 4.0 kB/s
cullens@cullens-laptop:~$ mkdir cdrom
cullens@cullens-laptop:~$ sudo mount /dev/cdrom cdrom
[sudo] password for cullens: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type
cullens@cullens-laptop:~$ sudo umount /dev/cdrom
umount: /dev/cdrom: not mounted
cullens@cullens-laptop:~$ 

```

Any ideas?

---

### Post by Alterax on 2009-05-06
ah...FF7.  Beauty of a game.

The only thing I am seeing in common here is the cd-rom drive itself.  This could mean that the drive is either going bad or the disk you are copying to cd is messed up...even though Sony wrote sections of bad tracks on the disks on purpose (copy protection), it shouldn't matter since dd is making the iso from a raw bit-for-bit image.

Grab any other disk you happen to have lying around, and see if you can mount it and make an iso using the same methods you did.  If it works, then the problem is your disk--which may be causing some of the latency issues you were having in the emulator.  If it doesn't on the other hand, your culprit is likely to be the cd-rom/dvd drive.

---

