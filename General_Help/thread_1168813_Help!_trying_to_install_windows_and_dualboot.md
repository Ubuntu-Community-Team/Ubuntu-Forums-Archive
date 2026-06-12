---
title: "Help! trying to install windows and dualboot"
date: 2009-05-24
forum: General Help
---

### Post by WRG on 2009-05-24
I am running just Ubuntu 9.04 on my laptop.  I downloaded windows 7 and made a boot cd.  I tried to install it but it wont let me.  When selecting which partition to put it on it wont.  Says must be formatted as NTFS.  Anyone know how to format the partition to enable me to put windows on?



Thanks

---

### Post by dhughes on 2009-05-24
You have to install Windows first and then Linux (Ubuntu), I would use Gparted on the LiveCD to partition the drive into two partitions and then install Windows first then Linux.

FYI to be perfectly clear I mean to start over, wipe your drive/partition then install the Operating Systems.

---

### Post by WRG on 2009-05-24
how do I wipe everything off and restart?

---

### Post by irv on 2009-05-24
Yes, this is good advice to install Windows first the and then Ubuntu Linux. Ubuntu is much more friendly with Windows that Windows with Linux. Microsoft doesn't want you to duel boot with anything else. It wants the PC to it's self. And yes, do the partitioning with gparted from Ubuntu then install Windows on the NTFS. Afterward do the install of Ubuntu.

---

### Post by WRG on 2009-05-24
I am trying to use gpart, but why is all the menu items darkened?  I wont let me click or change anything.

---

### Post by lindsay7 on 2009-05-24
Go to the Gparted web site and download the iso file. burn it to a disk. It will boot up your computer form the cd drive. Reformat the drive and install windows and Ubuntu. You need to make sure that the drive is unmounted before you can do anything. Right click on the drive and choose unmount.  You need to have some type of disk burner that will burn ISO files.  If you do not, look around the internet for one that is free.

---

### Post by WRG on 2009-05-24
when I try unmounting it i got this message:

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

---

### Post by Old_Grey_Wolf on 2009-05-24
Are you running gparted from CD?

And, if you want to keep any of your 9.04 settings or files you need to copy them to another disk/USB, before, partitioning.

---

### Post by lindsay7 on 2009-05-25
No, not manually. It is easiest to use the Gparted live cd that I suggested you download. NOT the Ubuntu live cd. I believe when you use the Gparted Live cd all the drives and partitions will be unmounted. It is good to have a copy to the Gparted live cd around. It comes in handy.

---

### Post by irv on 2009-05-25
> **lindsay7 said:**
>  It is good to have a copy to the Gparted live cd around. It comes in handy.

I agree with that! I even use it when I am working on a Windows PC with a very large drive. Now with Ext4 coming gparted will probably supporting it. It's a good utility to do the hard drive stuff before ever installing any OS.

---

