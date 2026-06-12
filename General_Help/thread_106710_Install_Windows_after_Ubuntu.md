---
title: "Install Windows after Ubuntu"
date: 2005-12-21
forum: General Help
---

### Post by DarkAngel88 on 2005-12-21
Hi everybody !!

I recently make the move of trying Ubuntu and I really like it !  Recently, I mixed up x server and nothing was working anymore so I decied to format the whole HD and only put Ubuntu.  But now that I think about it, I still need windows for some applications.  I'm now wondering if there is a way to install Windows and keep Ubuntu without messing grub ??  

Please consider I don't want to use any other options like vmware, wine or things like that.  I want to dual boot both OS but I wanna do the reverse steps (Windows AFTER Ubuntu).

Thank !!

DA

---

### Post by BathroomNinja on 2005-12-21
It's normally harder to do things this way, reason being that Windows won't see linux and may try to over write it.

Tell me how you have your system configured.

How many hard drives do you have?
What size?
How are the partitions setup?

EDIT- if you don't know, you can use gparted or you can type 'cat /etc/fstab' at the terminal to get some basic info

---

### Post by DarkAngel88 on 2005-12-21
I got one 60 GB harddrive with 2 partitions (swap and ext3).  I wanted to partition my HD into 2x30 GB (well, 30 GB and 28.5 GB + 1.5 GB swap) with gparted under ubuntu.

---

### Post by simms on 2005-12-21
[QUOTE=BathroomNinja]It's normally harder to do things this way, reason being that Windows won't see linux and may try to over write it.[/QUOTE]

i agree.  
note that the Winblows installer will likely stab your existing [Ubuntu] MBR in the back without even telling you and replace it with its own crooked MBR.

for this reason your probably best off installing Winblows on a separate drive, with your Ubuntu drive unplugged for the duration of the install.  then, once you're done, you reconnect the Ubuntu drive, force a Ubuntu boot (this may require a temporary disconnect of the Winblows drive), and reconfigure GRUB so that you can pick the OS to use at startup time.

---

### Post by DarkAngel88 on 2005-12-21
I'm doing this on my laptop... only way I can see is using a external HD... but I'm pretty sure there is a way of doing this without using a secondary HD ??

---

### Post by BathroomNinja on 2005-12-21
You can do it.  First question, how much data do you have on the laptop?
There are 2 ways of doing this that I know of (there may be more).

1.  Backup your data to CD, or whatever.

Boot up the computer with the Live Ubuntu CD.  Once you get into Gnome, run gparted to re-partition your HD into how you want it.

Reboot the system without the CD, to make sure your system still boots into Ubuntu.

Reboot the system with your Windows CD.  Install windows into one of the new partitions you created.

Reboot and there is a really good chance windows will come up without giving you the option to boot into Ubuntu.  You will have to reboot with the Ubuntu Live CD and grab a copy of your kernel and copy it over to your windows partition among other things.  I won't go into it at the moment.



Option 2
Backup your important files.

Reboot laptop with Windows CD.  Use windows installer to create your partitions. (just create the partion you want for Windows, leave the rest as unpartitioned space for Ubuntu)

Install windows.

reboot with Ubuntu CD.  Install Ubuntu.  

The world is happy



Let me know which option you would like to do.  Honestly, if you don't have many files to backup, it will be a LOT faster and easier to just let windows wipe linux and install Ubuntu afterward (option 2)

---

### Post by DarkAngel88 on 2005-12-21
I have to agree... it would be better to do option 2.  I first wanted to installing windows without wiping out linux but like you said, it would be much easier to do it the "right" way.  I guess I'll just try to back up as much thing as possible and do what you told me to do.

Thank you guys for your infos... looks like I have to make concessions to make the world happy ! ;)

---

### Post by BathroomNinja on 2005-12-21
Don't feel bad.  I've had to do the same thing.  It really sucks that Windows can't see it.  I spent many days trying to get it to work before I just wiped it and started over again.

Also of note.  On one of my desktops, I share about 200gigs of space between Windows (which I have not used in over a month) and Ubuntu.  Windows won't let you use FAT32 to format a drive larger than 38(?) gigs or so.  The work around if you want a shared drive, is to format the partition in Ubuntu as EXT2.  There is a driver you can download for Windows that allows it to read and write to EXT2 with no issues.  Works GREAT for me.  Let me know, I'll find the link for you.

EDIT- found it. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by DarkAngel88 on 2005-12-21
Thanks for your hint BathroomNinja !!  I'm trying to see how I would setup my hd so that I can access my linux partition under win (solved, thanks to you) and to access my win partition under ubuntu (which, I think, could be resolved if I install win on a fat32 partition right ?  Cause with what I have read, I cannot R-W on a NTFS partition...)

Am I right ??

Thanks !

---

### Post by BathroomNinja on 2005-12-21
[QUOTE=DarkAngel88]Thanks for your hint BathroomNinja !!  I'm trying to see how I would setup my hd so that I can access my linux partition under win (solved, thanks to you) and to access my win partition under ubuntu (which, I think, could be resolved if I install win on a fat32 partition right ?  Cause with what I have read, I cannot R-W on a NTFS partition...)

Am I right ??

Thanks ![/QUOTE]


Correct.  Your best bet would be to make a small partition for windows during the install with FAT32.  Then, when you install Ubuntu, create the 'shared' partition as EXT2.  Then, when you boot back into windows, install that driver, now it sees the shared partition.

You can easily add the fat32 partition to your fstab.  I'll link you in a few minutes.

EDIT- Here is a great guide by user aysiu: [http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)
EDIT2.0- it's basically just adding '/dev/hdb1 /whatever/directory vfat iocharset=utf8,umask=000 0 0'

---

### Post by DarkAngel88 on 2005-12-21
Great idea !!

Looking forward tonight for doing this !!

PS : I looked at the link about the ext2 filesystem and it's telling me that it works with both ext2 and ext3... but.. what is the difference between those 2 fs ??

Thanks

---

### Post by ksudbury on 2005-12-21
Ext3 is basically ext2 plus a journal.

---

### Post by DarkAngel88 on 2005-12-21
So... either if I install the ext2 or ext3 FS it won't affect the functionnality...   

Thank you !

---

### Post by BathroomNinja on 2005-12-21
Correct.  I don't remember why I decided on ext2 instead of ext3 but I'm sure I had a reason.  I'm sure either should work fine.

---

### Post by farnsworth on 2005-12-21
Hi guys,

This won't work for you, DarkAngel (I'd take BathroomNinja's option2), but for those of us who need windows and have a second drive, here's how I did it.

I distilled this method from an hour of combing other forums.  It might not be the safest method, so caveat emptor, YMMV, etc...

I should also say that if you want to freely exchange files between the two OS', set up a second fat32 partition on the windows drive _in windows setup_.  ntfsresize is a great program, but you'd rather _not_ be forced to use it.

1. turn off your computer and the power supply

2. open up your box and disconnect your ubuntu drive
we'll leave it disconnected until step 6

3. connect your backed-up, soon-to-be windows drive to ide1; or if it's on the same ide port, just make sure the _end_ of the ribbon cable is connected
NOTE: for an older drive, set it to 'master'(the pins on the back)

4. turn on the power supply, slap in the windows install cd, and install

5. do whatever you need to set up windows to your 'liking', and turn off the computer and power supply (I recommend placing a second fat32 partition on the drive for read/write access from ubuntu)

6. reconnect your ubuntu drive to ide1, or the _end_ of the ribbon cable; connect the windows drive to ide2, or the _middle_ of the cable
NOTE2: for the older drive, re-set it to 'slave'

7. boot up the computer; you're in ubuntu

8. here's the fun part.
```
~$ sudo gedit /boot/grub/menu.lst
```
add your windows boot selection
```
title		Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
rootnoverify (hd1,0)
makeactive
chainloader +1
```
notice the two 'map' lines; we're telling windows it's on hd0

9. if you want your windows partitions automounted in ubuntu:
make a mountpoint for each partition
ex.
```
~$ sudo mkdir /mnt/xpntfs
```
open your fstab
```
~$ sudo gedit /etc/fstab
```
add a line for each partition
ex.
```
/dev/hdb1       /mnt/xpntfs     ntfs defaults,rw,user,umask=000 0 2
/dev/hdb5       /mnt/xpfat32    vfat defaults,rw,user,umask=000 0 0
```

10. reboot a few times and make sure everything works:smile:

edit: added "NOTE2"

---

### Post by BathroomNinja on 2005-12-21
great walkthrough farnsworth!  I wish I would have thought of that when I did my desktop.  You are correct in that it won't help out DarkAngel, but I will be bookmarking this thread for reference.  Thanks

---

### Post by farnsworth on 2005-12-21
I'm happy to contribute.  Nothing about windows irks me more than it's inability to install on a non-root partition.:mad:

---

### Post by DarkAngel88 on 2005-12-22
Wow, that is a gold mine indeed !!  I was looking forward to do the same thing on my desktop but now I'll sure try this !!  It was indeed useless for my laptop but it will sure help on my desktop !!

Thank you all guys for helping me out...  I sould now look forward for my first contribution in the Ubuntu communauty !  

Merry Christmas !

DA

---

### Post by fordfan753 on 2005-12-22
There are two ways I've done this, one time I made myself a grub floppy and used grub command line to boot into Ubuntu. After that I did a "grub-install /dev/hda" to reinstall grub on my hard drive and take back the MBR.

The second time I booted the live CD and I used grub-install /dev/hda from that I think. I'm not really certain about this one, it was a while ago.

Just goes to show that floppy disks never die!

---

### Post by matthinckley on 2005-12-22
You can use parted from the live cd to resize your ext3 partition, then just install windows into the new free space

once this is done you will not be able to boot into ubuntu.. but this is easy to fix..

1. boot the live cd
2. go to a terminal and mount your ext3 partition
       sudo mount -t ext3 /dev/hda1 /mnt
3. change the root to your hard drive
       sudo chroot /mnt
4. re-install grub to the mbr
       grub-install /dev/hda
5. edit menu.lst in the /boot/grub directory and add your new windows installation to it...
        I can't remember what the entry actually says.. I don't have windows on my computer anymore.. but anyone that dual boots can look in theirs and post it here.
6. reboot and you are good to go!  :)

edit: you can use gparted from the live cd.. I've personally had better luck using parted from the live cd command line.

---

