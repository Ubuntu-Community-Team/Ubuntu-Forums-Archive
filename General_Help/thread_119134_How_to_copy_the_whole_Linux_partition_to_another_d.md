---
title: "How to copy the whole Linux partition to another disk? I didn't have luck with Parted"
date: 2006-01-18
forum: General Help
---

### Post by Turin Turambar on 2006-01-18
My current Maxtor hard drive has some faults (SMART detected it and powermax verified it), so I bought another one - Western Digital.
I alredy copied the entire WinXP partition with MaxBlast disk-to-disk copy program.

HOW to do that in Linux?
With "cfdisk" I made a Linux & swap partition. I then converted it to EXT3 with "mkfs.ext3" program and formatted the swap partition wiith Disk Manager.
I tried to copy with "parted", but failed, because it demanded the source drive to be unmounted - I couldn't do that! I'm working in linux, I cannot umount the whole system!

Did I miss something here? Or is there any other program that could do disk-to-disk copy of Linux partitions?

And one other thing: IF I manage to copy it entirely, how to make a drive bootable with grub menu (so I could select the OS)?

Thanks!!

---

### Post by linuxden on 2006-01-18
Ok you could just backup your system... 

Using "tar" and then burn that to CD/DVD then install your new hard drive and install Ubuntu + restore backup....

---

### Post by pappo on 2006-01-18
I have done what you are trying before, but I used the System Rescue disk (see [http://www.sysresccd.org/](http://www.sysresccd.org/))  partimage is the Ghost clone for Linux

Just use your windows side to get the SystemRescue CD iso, make a cd and then boot off that CD.
You can then pull partitions off one disk, and save them onto your new disk.
All you need to do is make sure your new disk partition is the same size as your old linux partition on your original disk.

Good luck.

---

### Post by rattking on 2006-01-18
check it
cp -ax / /new-disk
will do
make sure /new-disk/proc exists but is empty

[http://www.storm.ca/~yan/Hard-Disk-Upgrade.html](http://www.storm.ca/~yan/Hard-Disk-Upgrade.html)
for the full howto

as for parted you could boot from a live cd and run it from there.. might be easier

---

### Post by Turin Turambar on 2006-01-18
[QUOTE=rattking]check it
cp -ax / /new-disk
will do
make sure /new-disk/proc exists but is empty

[http://www.storm.ca/~yan/Hard-Disk-Upgrade.html](http://www.storm.ca/~yan/Hard-Disk-Upgrade.html)
for the full howto

as for parted you could boot from a live cd and run it from there.. might be easier[/QUOTE]

Ah - damn it. The ubuntuforums went down so I had to figure out something myself.
What I did was - cp / /newdisk!

Well, now, everything is working ok, as it should. However, the linux ext3 partition has 10gigs of total space, but the disks-manager reported that only 2.5gb's were free! How?? There's no chance that I filled 7.5gigs! I checked all the directories, and I found only like 3gb's used. ???:confused:

Now when I look at it, I'm sure proc was NOT empty when I did the copy thing. Maybe that's why I'm getting such enormous used space? Can I fix this somehow?

---

### Post by rattking on 2006-01-19
/proc/kcore is the same size as the amount of RAM you have.. if coppied that could eat a lot of space
I would boot from the old drive or a live cd mount the new disk and delete everything in /newdisk/proc
also check that cp didn't try to copy everything twice.. eg. /newdisk to /newdisk/newdisk
hope that helps..
or try and recopy with cp -ax to be sure the symlinks, mode, ownership, timestamps are all preserved

---

### Post by Turin Turambar on 2006-01-19
Hey, thanks for help.
I checked everything and didn't notice anything unusual - proc dir is empty, including many others. In fact, I checked the whole Linux partition in WindowsXP with Total Commander. When not in order, linux eats about 1.6gb of my drive. That's MUCH lower than 7.5gb or more!

I have started some other thread about this issue here...  
[http://www.ubuntuforums.org/showthread.php?t=119342]("http://www.ubuntuforums.org/showthread.php?t=119342")

---

