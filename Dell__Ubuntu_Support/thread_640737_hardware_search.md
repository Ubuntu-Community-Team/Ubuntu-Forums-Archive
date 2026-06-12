---
title: "hardware search"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by crawall on 2007-12-14
I'm a real newbie. I installed ubuntu to my laptop that i 'found' again. It's was quiet dusty and i don't remember the specifics of all the hardware. It's a dell latitude D505; is there a way that i can check it for all the hardware and get everything set up within ubuntu. No windows installed.

---

### Post by linuxwizard on 2007-12-14
[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505)

in terminal > lshw > will lists hardware on your system

---

### Post by natehall on 2007-12-14
That's a neat command ! Thanks. Off the subject here but I'm trying to take a peak at a partition that does not normally load. I've tried mount  /dev/sda2  but that just gives me an error. ( can't find /dev/sda2 in /etc/fstab or /etc/mtab ) I don't have to modify those files do I? I'd rather not!

---

### Post by Paul S on 2007-12-14
sudo mount /dev/sda2 /media/sda2

---

### Post by natehall on 2007-12-16
> **Paul S said:**
> sudo mount /dev/sda2 /media/sda2

mount: mount point /media/sda2 does not exist

---

### Post by gbrainin on 2007-12-16
> **natehall said:**
> mount: mount point /media/sda2 does not exist

The mount point does need to exist before the mount command will work.  A mount point is just a directory, and you create a directory with the mkdir command.  Since /media is most likely owned by root, you'll need to have root powers to create a subdirectory.  So:
```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
```

When you're done looking, you should be able to unmount the partition with the umount command (note that it is umount NOT unmount):
```
umount /media/sda2
```

Note that if the partition is NTFS, I believe you still get read-only access to it.  Also, in general, be extremely careful of what you do with the sudo command.  It's the only thing standing between you and deleting an important system file, or reformatting your drive, or some other catastrophic action.  Taking the time to read up on basic system commands like mkdir, mount, etc. goes a long way toward avoiding mistakes.

---

### Post by natehall on 2007-12-17
When you're done looking, you should be able to unmount the partition with the umount command (note that it is umount NOT unmount):
```
umount /media/sda2
```
 Thanks ! I have a 1420N with a FAT W95 partiton. I thought it was a partition for the Windows system that was not installed. In fact it is for the Dell recovery Ubunutu preload.

---

### Post by gbrainin on 2007-12-17
> **natehall said:**
> Thanks ! I have a 1420N with a FAT W95 partiton. I thought it was a partition for the Windows system that was not installed. In fact it is for the Dell recovery Ubunutu preload.

You're welcome.  I didn't realize yours was a Dell pre-install.  The factory partition table is explained here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions"), and there's all sorts of other useful stuff on that wiki.

---

### Post by crawall on 2008-01-06
Thansk for the information.
It took me a while to reply there i was out of the country

thanks again

---

### Post by crawall on 2008-01-23
thanks again, i forgot to close the post

---

