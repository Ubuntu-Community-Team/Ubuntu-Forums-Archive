---
title: "[SOLVED] Need help re-formatting Flash Drive"
date: 2009-01-04
forum: General Help
---

### Post by Oldcowboy on 2009-01-04
I keep backups of important data on several flash drives. On one, I also have Puppy, which can be carried around to use on other computers.

For some reason, this drive was formatted as FAT16, which made it show up as /media/USB DRIVE
rather than the other flash drives /media/disk (which were formatted as ext3)

To facilitate writing a batch file to do the backups, I wanted them all to be a consistent /media/disk. After copying all of the files and directories from the flash drive to a temporary partition in UBUNTU 8.10, I went back to my dual-boot openSUSE 11.0, where I knew how to format disks (so I thought.) But during the formating of the flash drive to ext3, it locked up. Then, I was forced to reboot to get out of the lockup. Now, this flash drive is in limbo, and is not recognized.
How can I format it (preferably learning how in UBUNTU) to ext3, so that I can copy my files back to it?

Thanks,

---

### Post by lsutiger on 2009-01-04
Have you ever used gparted?

sudo apt-get install gparted

once installed run gparted in terminal
sudo gparted

From there you'll have a gui to navigate around.
hope this helps

---

### Post by Oldcowboy on 2009-01-04
Thanks for the good try, but inasmuch as my flash drive became corrupted during my previous attempt to re-format it in openSUSE, it doesn't even show up in gparted.

---

### Post by lsutiger on 2009-01-04
what do you get from lsusb?

---

### Post by Oldcowboy on 2009-01-04
brooks@brooks-desktop:~$ lsusb
Bus 002 Device 003: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brooks@brooks-desktop:~$

---

### Post by lsutiger on 2009-01-04
I am guessing the flash in question is the 1 GB drive?

---

### Post by Oldcowboy on 2009-01-04
I would assume the same thing. :popcorn:

---

### Post by lsutiger on 2009-01-04
What do you get from df -h

---

### Post by Oldcowboy on 2009-01-04
brooks@brooks-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10             20G  7.3G   12G  39% /
tmpfs                1005M     0 1005M   0% /lib/init/rw
varrun               1005M  100K 1004M   1% /var/run
varlock              1005M     0 1005M   0% /var/lock
udev                 1005M  2.8M 1002M   1% /dev
tmpfs                1005M  276K 1004M   1% /dev/shm
lrm                  1005M  2.4M 1002M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda11             20G  198M   19G   2% /boot
/dev/sda12             20G  2.2G   17G  12% /home

---

### Post by lsutiger on 2009-01-04
I am at a loss myself. The computer sees the drive but does not mount it. I am actually writing this to get this thread bumped. I will be watching.

I will offer this, though I hate doing this...have you tried the flash drive in an M$ system?

---

### Post by Oldcowboy on 2009-01-05
I no longer have a M$ system, but will try it in a friend's computer at the first opportunity.

First, I may go back to openSUSE and try to re-format it there with a different mount point and see what happens.

Please understand that I do appreciate all of the responses that I have gotten, even if none has provided an easy "Magic Bullet."

Flash drives are now cheap enough that I may toss this one if I cannot solve the issue. It is just a feeling of challenge that  keeps me going.:)

---

### Post by Oldcowboy on 2009-01-05
Not to be dissuaded, I went back to openSUSE and re-formatted the flash drive as ext3, choosing a mount point of /local. That could be what threw me before, because a mount point of /media was not among the offered options, and I mistakenly thought that the mount point would be embedded with the drive.

Then, going back to UBUNTU, the drive was recognized, so I attempted to copy all of my files back to it. No luck.:( Then, I checked permissions on the flash drive and was reminded that root was the owner. After changing the owner to myself,
I did cp -r * all of my files and directories back to the flash drive. :D Just to double check, I booted from the Puppy CD with the flash drive inserted, and all of my data and settings were intact.

Thanks again to all who offered assistance.
You kept me going until it was solved.

---

### Post by lsutiger on 2009-01-05
Awesome! I learned from this one!

With linux, you can only get smarter :)

---

