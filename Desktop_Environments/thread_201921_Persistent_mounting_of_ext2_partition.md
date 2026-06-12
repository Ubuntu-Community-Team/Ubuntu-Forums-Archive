---
title: "Persistent mounting of ext2 partition"
date: 2006-06-22
forum: Desktop Environments
---

### Post by presentt on 2006-06-22
Hello,

I have a 9GB ext2 partition on /dev/sda6 that I need to mount in Ubuntu as /mnt/data.  It mounts correctly, but as soon as I reboot it unmounts.  Can I make the mount persistent?

To mount it, I open System - Administration - Disks - Partitions, and select "Partition 6" (that's where /dev/sda6 is).  I enter in the Access Path "/mnt/data," which is already a directory on my filesystem.  Next to Status, the Disk Manager says "Inaccessible" until I click on Enable.  Then I can view all of the files in /mnt/data using a terminal or the File Browser--**until a reboot*.***

After rebooting, I have to remount the directory, or else ```
ls /mnt/datap
``` comes up empty.

Anybody have a suggestion?  It's not a big deal to remount it, but it'd be easier if I didn't have to.

---

### Post by jvl on 2006-06-22
add 

/dev/sda6 /mnt/data ext2 defaults 0 4 

line to /etc/fstab and then mount it with mount -a (for the first time)
should be mounted automagically on next reboot.

---

### Post by presentt on 2006-06-22
[quote=jvl]add 

/dev/sda6 /mnt/data ext2 defaults 0 4 

line to /etc/fstab and then mount it with mount -a (for the first time)
should be mounted automagically on next reboot.[/quote] 
Thanks, that worked perfectly.  What does the 0 and 4 mean, though, or is there somewhere I can look that explains the fstab file and its usage?

---

### Post by jvl on 2006-06-22
first number is there for historical reasons - its switch that says whether the fs should be dumped by dumpfs or not (0 = no, 1 = yes). The other number says in what sequence should the fs be checked by fsck during boot. I guessed 4, so it would be disk in your setup.

The point is that you could fsck two filesystem on two different disks simultaneously, checking two filesystems (partitions) on same disk would make those two fsck processes fight for the I/O operations. 

so if you have filesystems let's say hda1, hda2 and hdb1, the numbers could be like this:
hda1 0 1
hda2 0 2
hdb1 0 1

hda1 and hdb1 could run simultaneously, hda2 would run when the first "batch" finishes. Zeroes are there because we won't be using dumpfs ;)

Hope it's clear enough, if not, don't be affraid to ask.

---

### Post by presentt on 2006-06-22
[quote=jvl]The other number says in what sequence should the fs be checked by fsck during boot[/quote] 
Thanks.  I looked again at the /etc/fstab file.  A bunch of the entries have 0's for that number.  Does this mean fsck doesn't check them, or checks them first?  

Also there's no listing with a 3 for that number.  Can I change the entry you told me to put in (the one with the 4) to a 3, and would that make any difference in terms of speed or efficiency?

---

### Post by jvl on 2006-06-23
The first zero on the line is okay. You don't have a problem. But, if you have an ext2,ext3 partition, there should be some kind of number, so it could be checked automagically on boot up. 

the numbers are only compared, they don't have to be in one line. 1 3 5 will be checked in 1 3 5 sequence. If you change it to 1 2 3, the result will be the same. So basically, if that 4 is going on your nerves, change it to 3. The effect will be the same. 

When I gave you the line, I had to make something up, because if I gave you 0 0, the filesystem won't get checked. So as I said earlier, I wanted this partition to be checked last, so it would not interfere with any other cheks.

If you're mounting ntfs or fat partitions, they usually would be listed as 0 0, because fsck doesn't know how to check and fix those partitions. (Need to use scandisk under windows for that)

If still in doubt, post your /etc/fstab and ask.
have a good day

---

### Post by presentt on 2006-07-03
Awesome.  Good to learn, thanks a lot.

---

