---
title: "Could not find ubuntu partition on Grub load"
date: 2009-05-27
forum: General Help
---

### Post by dilomo on 2009-05-27
Yesterday the electricity stopped suddenly and today after I booted my computer I got a grub> .... console and nothing is loaded. I tried 
```
find /boot/grub/stage1
```
to find my partitions but they do not appear to be there.

I created a live CD but it does not want to start either and I'm stuck now. I have some important data that I would like to recover but don't know what to do. Any ideas???

---

### Post by VMC on 2009-05-27
> **dilomo said:**
> ...
```
find /boot/grub/stage1/
```
to find my partitions but they do not appear to be there.

...What output does the above message say? Also, what FS are you using - ext2/3/4/etc

---

### Post by hal8000 on 2009-05-27
I dont know if the live CD you created is customized to your distribution.

However, I do know that the live Ubuntu CD will work even without a hard drive. Put in the live Intrepid CD, boot from it and try:

sudo fdisk -l

Should list your hard drive partitions.
The output from
dmesg

may also be useful in solving this.
Normally,
find /boot/grub/stage1

should find your root partition, (in the form hdx,y)
root (hdx,y) from above command will tell grub where the root partition is, and
setup (hdx)  will install grub in the mbr

---

### Post by dilomo on 2009-05-27
> **VMC said:**
> What output does the above message say? Also, what FS are you using - ext2/3/4/etc

It says File not Found error and my fs is ext3 with Ubuntu upgraded from 8.10 to 9.04 and primarily installed from Wibu. 
I think that it cannot find any /boot partition at all. When I type ls it list the files in my Windows C: partition but my Ubuntu is in D:.

> However, I do know that the live Ubuntu CD will work even without a hard drive. Put in the live Intrepid CD, boot from it

As far as the LiveCD I have downloaded and installed Ubuntu 9.04 32-bit on a CD-RW disk but when Press enter on the first option of the menu the UI freezes. No Idea why but I can't check for defects either it will just freeze ...

---

### Post by Bender2k14 on 2009-05-27
> **dilomo said:**
> As far as the LiveCD I have downloaded and installed Ubuntu 9.04 32-bit on a CD-RW disk but when Press enter on the first option of the menu the UI freezes. No Idea why but I can't check for defects either it will just freeze ...

The Desktop version of Ubuntu 9.04 32-bit?  That ISO is 699 MB and the only CD-RW disks that I know of only hold 650 MB.  How many MB can your CD-RW hold?

Does Windows still work?...because a power failure can cause hardware problems which can express themselves it odd ways.

---

### Post by dilomo on 2009-05-27
> **Bender2k14 said:**
> The Desktop version of Ubuntu 9.04 32-bit?  That ISO is 699 MB and the only CD-RW disks that I know of only hold 650 MB.  How many MB can your CD-RW hold?

Does Windows still work?...because a power failure can cause hardware problems which can express themselves it odd ways.

On the disk it's written 700MB-80min.

And yes Windows works. i'm writing from there. My current menu.lst file does not contain the usual entries but this:

```
title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title REBOOT
	reboot

title HALT
	halt
```

Only the second option works and does not give file not found error.

---

### Post by Bender2k14 on 2009-05-27
> **dilomo said:**
> On the disk it's written 700MB-80min.

Ok, that should work then.  Not that this matters, but are you sure it is a CD-RW where RW=ReWritable as opposed to a CD-R where R=wRitable?

> **dilomo said:**
> My current menu.lst file does not contain the usual entries but this:

Can you post the whole file to make sure that I am understanding what I am looking at?

---

### Post by dilomo on 2009-05-27
> **Bender2k14 said:**
> Ok, that should work then.  Not that this matters, but are you sure it is a CD-RW where RW=ReWritable as opposed to a CD-R where R=wRitable?



Can you post the whole file so make sure that I am understanding what I am looking at?

I'm pretty sure as I have erased it before I wrote the iso file ;)

The only missing lines are from the beggining of the file:```
debug off
hiddenmenu
default 0
timeout 3
fallback 1
```

P.S. that file is located in D:\ubuntu\winboot\menu.lst

---

### Post by Bender2k14 on 2009-05-27
As for the CD, try reburning it.

As for your menu.lst file, I guess I am not sure what it is supposed to look like for the Wibu installation.  I can work some more on this tomorrow (16ish hours from now).  However, I do not think that you should be able to see your menu.lst file from Windows.  I thought the whole Ubuntu file system appears as a single file in Windows.

---

### Post by dilomo on 2009-05-28
It appears that my partitions got deleted permanently somehow :( Nothing more to do but to install ubuntu again after 1 year of no problems.

---

### Post by Bender2k14 on 2009-05-28
Wbui is great, but if you are going to reinstall Ubuntu anyway after using it for a year, then you might as well install Ubuntu into its own partition.  Remember, one of the benefits is that Ubuntu will be faster.

What version of Windows are you using? If you are using Vista, I recently learned that Vista supports resizing live partitions using the Disk Management (Control Panel -> Administrative Tools -> Computer Management -> Disk Management).

---

### Post by dilomo on 2009-05-28
> **Bender2k14 said:**
> Wbui is great, but if you are going to reinstall Ubuntu anyway after using it for a year, then you might as well install Ubuntu into its own partition.  Remember, one of the benefits is that Ubuntu will be faster.

What version of Windows are you using? If you are using Vista, I recently learned that Vista supports resizing live partitions using the Disk Management (Control Panel -> Administrative Tools -> Computer Management -> Disk Management).

I know that because before I used such type of configuration but in the time I had to install Ubuntu I just didn't have any cds so I decided to give wibu a try. 

Also I think I'm going to use that Disk management tool to free up some space for Ubuntu but where it is most appropriate drive C: or D: ? In C I have installed windows.

---

### Post by Bender2k14 on 2009-05-28
> **dilomo said:**
> where it is most appropriate drive C: or D: ? In C I have installed windows.

What are the sizes of each drive?  Are C: and D: each the entire capacity of two different physical drives?

---

### Post by dilomo on 2009-05-28
they have about 40GB free each. It's one 160GB drive.

---

### Post by Bender2k14 on 2009-05-28
I can't remember if this is necessary, but I always install each operating system in its own partition in a logical drive that is the entire partition.  So, I would not install Ubuntu to C:.

Are C: and D: in different partitions or the same one?

---

### Post by dilomo on 2009-05-28
Well they are different in order to keep my data safe in D: so I guess I have to install in C but when I use the Disk Management it won't allow me to spare more than 12 GB. So I guess I'll use the Ubuntu installation's partitioner and space allocator?

---

### Post by Bender2k14 on 2009-05-28
[QUOTE=dilomo]when I use the Disk Management it won't allow me to spare more than 12 GB.[/QUOTE]

Windows can only give you the extra space at the ends of the partition.  In order to maximize this extra space, you should defrag the drive first.  Even so, Windows also has some "unmoveable" files, so it is possible that defrag will not help you get more space.

If you want a partition for your data, then I would recommend getting enough space to create a third partition E:.  Trying getting more space from D: as well.

---

