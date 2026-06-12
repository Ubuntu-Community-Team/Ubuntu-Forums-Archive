---
title: "GParted problem..."
date: 2005-10-09
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-10-09
Good <insert>current time of day</insert>,

Here is what I am trying to accomplish,

I want to do this:
"Howto: Move /home and secure your files and configuration"
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

My 40 GIG drive is partitioned like this:
/dev/sda1 13gig (boot) (for / and /home)
/dev/sda5 1.1gig (swap)
/dev/sda3 12gig (not partitioned)
/dev/sda4 11gig (fat32 partition)

Okay--so the /dev/sda3 I want to use as my /home following the directions above.  I'm using gparted (GUI parition app) to change the /dev/sda3 to a 12 gig partition using the ext3 filesystem.  When I apply the changes the partition is created, but during the format (or convert or whatever it does) to ext3--every single time I try and do this something ODD happens.  90% of the time my system locks up dead. The other 10% of the time I get an error dialog that says "there was an error" and then my hard drive disappears.  And Ubuntu freaks out because it can't find anything because my hard drive just isn't there.  So I power off, reboot and everything is up and running again.  no problem.  Then I try to partition the drive again, same problem!  

I'm nervous about using the ubuntu fdisk because I don't want to kill my other partitions.  And I couldn't find a "how to" or any other good documentation on using it.   It's different than the msdos fdisk, which I do know well.

Also because my system locks up everytime and I have to reboot after attempting this I'm not sure where to look in a log file for what the specific error is, if anyone knows where to look for this that would be appreciated as well.

Any ideas?

Thanks for the input and direction.

Aaron ](*,)

---

### Post by 11hjpphty76lkjj on 2005-10-09
Sorry I should have put this on my first thread.

My goal is to get that partitioned and formated to ext3 (prefer) or ext2.  So any help on doing that is greatly appreciated!

Aaron

---

### Post by brt on 2005-10-09
just use a terminal and the command "sudo fdisk /dev/sda" or "sudo cfdisk /dev/sda" to define the partitiontype (85) of /dev/sda3  and write your new partitiontable.

reboot to make sure your kernel has the new partitiontable.

execute "sudo mkfs.ext3 -j /dev/sda3" to create a journaling ext3 filesystem.

---

### Post by 11hjpphty76lkjj on 2005-10-10
If I could get some additional direction I would appreciate it.  Sorry I'm very nervous of messing with my partition table because I need my system to function as is otherwise.  I do the sudo fdisk /dev/sda3 and then I'm not sure exactly what to do.  I do n for new partition and then it asks me for partition number (which I don't know what to put in there) and then for first sector, etc. and I'm not sure what to put in there as well...if I put 1 it will be the first sector on this partition or on the hard drive?  I've been trying to find some better documenation on fdisk but I can't find it.

Thanks!

Aaron

```
aaron@c-24-22-56-78:~$ sudo fdisk /dev/sda3
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 1530.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): v
24579449 unallocated sectors

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (1-1530, default 1): ^X
[2]+  Stopped           
```

---

### Post by 11hjpphty76lkjj on 2005-10-10
hey I think I got it actually. I should have tried cfdisk it's much better.

Thanks!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-10
Well I got the partition created and then i'm trying to format it using the command above my system is freezing at this point:

"Writing inode tables: 82/94"

I'm guessing it's a hard drive issue..unless anyone else has any ideas?

Aaron

---

### Post by brt on 2005-10-15
if you did a reboot to let the kernel recognise the new partitiontable before formatting, then i would say its a problem with your drive...

---

### Post by az on 2005-10-15
mke2fs -c -c /dev/sda3

Putting two "-c" arguments will make it do a (destructive) read-write examination of the disk.  You will know if it has some bald patches...

---

