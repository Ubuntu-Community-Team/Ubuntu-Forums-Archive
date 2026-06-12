---
title: "Gave up waiting for root device . . . ALERT! /dev/disk/by-uuid...does not exist."
date: 2009-11-11
forum: Desktop Environments
---

### Post by peyre on 2009-11-11
Help!  I upgraded from Xubuntu 9.04 to 9.10 about a week ago, and seemed to be ok.  I had the issue some others reported where I it kept rejecting my credentials, but that wasn't a showstopper since it would let me in after 2-4 login attempts.  (Don't know if this is relevant, but otherwise the upgrade seemed to have gone nice and smooth.)

But tonight, it won't boot at all.  I turn on the computer, GRUB starts, I see the initial splash screen just before it challenges me for my credentials, then I'm dropped to a text-only screen saying the following:

```
Gave up waiting for root device. Common problems:e7f934993ab
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/46e28492-a3df-422b-a4b1-fe7f934993ab does not exist. Dr
opping to a shell!

BusyBox v.1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

```

WTH?  I've looked around and found lots of suggestions, but none have helped.  For instance, some have suggested editing certain things in vi, but my system says vi is not found.  Did my OS get hosed, or am I just in a limited environment that doesn't show me everything?  An ls at / gives me:

```
dev     lib     usr     etc     sbin    sys     tmp
root    conf    bin     scripts init    proc    var
```

You'll note no /home directory(!)

cat /proc/cmdline returns:
```
root=UUID=46e28492-a3df-422b-a4b1-fe7f934993ab ro quiet splash
```

cat /proc/modules returns:
```
usb_storage 52576 0 - Live 0xf8104000
floppy 54916 0 - Live 0xf80d9000
r8169 32064 0 - Live 0xf80b3000
mii 5212 1 r8169, Live 0xf80a1000
intel_agp 27484 0 - Live 0xf8091000
agpgart 34988 1 intel_agp, Live 0xf8079000
```

(Incidentally, this is a new computer with a single SATA drive which still had lots of free space available.  It also includes a floppy, Zip, DVD drives and a 15-in-1 card reader.)

---

### Post by peyre on 2009-11-11
Follow-up: I tried rebooting several times, and I've also tried (and failed) to get into recovery mode.  Recovery mode brings me to the same text screen and message.

When I boot from a live CD, there is a /home folder in the file system, but all that's in it is an ubuntu folder.  And Thunar shows my File System has only 1GB of free space--I wonder if something's happened to my swap partition, and Xubuntu has become convinced that that's my only partition on this drive.

If I boot with the Ultimate Boot CD for Windows, Disk Administration shows the two partitions--one 2.8GB, the other 460GB (which is about right).  Also, when I start the Xubuntu installation, the partitioner says there's no operating system installed on the disk(!)

Now, when I boot from the live CD, go to /dev$, and execute sudo cat sdb2 (the identity for my main drive, where Xubuntu was installed and where all my data is/was), it displays garbage characters (see attached).

Anyone know what's going on?  If I've lost everything and just need to start over from scratch that's fine--I can do that, and I have a fairly recent backup.  BUT, if there's anything I can do to repair my system in place, that'd be much better.  Anyone have any idea??

---

### Post by peyre on 2009-11-12
Bump?

---

### Post by HenkVuijk on 2009-12-03
Had the same problem after upgrading to Xubuntu 9.10
I noticed, that more and more often during boot I got the mesage ´device UUID .... not found´, untill the boot completely failed.:cry:

Then I changed fstab and replaced there in the line for the root device:
UUID .......
by
/dev/sda7
(this is my root device)

and then Xubuntu booted again, and already quite a few times, without complaints

henk

---

### Post by peyre on 2009-12-03
Well I'll be...hey, thanks!  Unfortunately I've already reformatted and started over from scratch, but I'll write this down in case I run into it again.

---

