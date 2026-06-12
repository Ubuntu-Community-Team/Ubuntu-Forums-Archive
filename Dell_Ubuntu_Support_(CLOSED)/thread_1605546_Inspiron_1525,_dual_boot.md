---
title: "Inspiron 1525, dual boot"
date: 2010-10-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by flipflapje on 2010-10-25
Hello people,

Got some problems with dual booth (GNU GRUB version 1.98)
I installed Windows XP on my computer, now I decided to install Ubuntu 10.10.
I've installed Linux Ubuntu and Windows XP on the same partition.
Ubuntu works fine when I choose Linix in GNU GRUB, but Windows XP doesn't work any more, and I need both OS :(

When I choose Windows XP in GNU GRUB I'll get an error:
File: \Boot\BCD
Status: 0xc0000098
Info: The Windows Boot Configuration Data File does not contain a valid OS entry.

I dont know how to fix this.
Many forums say GNU GRUB sucks.

Does anybody know how to fix this?

Greetings,

Bjorn

---

### Post by mjkuwp on 2010-10-26
I'm also new to this.. so unfortunatly I cannot provide expert help.

However, I do have a 1525... so we have that in common.

First, I did not know it was possible to install two OS in one partition.  I assumed that was not possible.  The 'normal' installer may try to shrink your windows partition when it installs in order to create room to make it's own.

here's what I did on my computer after I installed a new, bard drive.

1. Installed VISTA using the entire drive.
2. Used VISTA to shrink the partition (I left 80GB unallocated)
3. downloaded the "ALTERNATE CD" for 10.10.  (this is very important) as an ISO and burned that CD
4. used the CD to install 10.10 - I selected ~"install in the largest free space"

The installer created two new partitions, one for the OS and one for swap. now the drive is in 3 partitions.

With XP, I do not know how you would shrink the main partition, but you could use the installer.

** Have you checked the filesystem to see if the windows OS is still there?

---

### Post by bobmartens on 2010-11-01
I recommend using different partitions if possible,  using Fat for the windows one. First boot from a live cd and create partitions in gparted   One primary Fat32 for windows, a Primary ext for linux, and an extended swap (2 gb should do).
 Install Windows first, then ubuntu from live cd, manually adjusting partitions: just set 'do not use this partition' option the windos one. I did this with xp, but vwith vista this should work too, I guess. This is not the only way to dual boot, and backing up data from win as well as ubuntu is possible with another approach. I can give you those instructions by simple request, but need to go now. Hope this helped you

---

