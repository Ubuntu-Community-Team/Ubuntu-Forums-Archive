---
title: "Change premissions on a mounted drive"
date: 2005-10-13
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-13
Howdy!

I got my new Maxtor 300 nice and formatted, but only the root can write to it which is a problem.

I tried to use a couple different things involving chmod but none worked :|

---

### Post by taurus on 2005-10-13
Can you be a little more specific on that?  How did you mount the drive and where did you mount it?

---

### Post by SeanCallan on 2005-10-13
Sorry :)

Someone helped me through the mounting so I can't recall all the steps actually.

I mounted to drive to /mnt/storage

I believe we called it hdb1.

---

### Post by taurus on 2005-10-13
Do you mount your second harddrive, /dev/hdb1, by hand or do you have the system does that for you (in /etc/fstab) when it boots?

---

### Post by SeanCallan on 2005-10-13
The system mounts it for me when I boot.

---

### Post by taurus on 2005-10-13
That's what I thought too.  Can we look at your /etc/fstab then?

---

### Post by SeanCallan on 2005-10-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2005-10-13
[QUOTE=SeanCallan]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/QUOTE]

Wait a second!  I don't see any /dev/hdb1 in there at all!!!  :confused:

---

### Post by SeanCallan on 2005-10-13
/dev/hdb shows up in my System -> Admin. -> Disks as the 300GB drive..

---

### Post by taurus on 2005-10-13
What is the output of this command then?

df

---

### Post by SeanCallan on 2005-10-13
/dev/hda1             74684224  34511192  36379284  49% /
tmpfs                   388212         0    388212   0% /dev/shm
tmpfs                   388212     12588    375624   4% /lib/modules/2.6.12-9-386/volatile


I really appreciate your help :)

---

### Post by taurus on 2005-10-13
[QUOTE=SeanCallan]/dev/hda1             74684224  34511192  36379284  49% /
tmpfs                   388212         0    388212   0% /dev/shm
tmpfs                   388212     12588    375624   4% /lib/modules/2.6.12-9-386/volatile


I really appreciate your help :)[/QUOTE]

Hmm...  Again, I don't see any /dev/hdb1 as well!  Could it be a network drive instead of a local drive, connecting directory to your computer?

---

### Post by SeanCallan on 2005-10-13
It's connected by IDE cables.  I stuck it in my case 2 days ago..

I can see it when I go to Disk Management, it's right there /dev/hdb

---

### Post by taurus on 2005-10-13
Maybe you want to take a screenshot of that because I can't seem to see it anywhere with /etc/fstab and df!!!  :confused:

---

### Post by SeanCallan on 2005-10-13
[http://www.georgiasouthern.edu/~nsmith22/images/disks.jpg](http://www.georgiasouthern.edu/~nsmith22/images/disks.jpg)

Someone mentioned I need to add it into the fstab

---

### Post by taurus on 2005-10-13
Okay, this is what I think your problem is!  You only connected your 2nd HD to your computer but you probably have not formatted it and mounted it.  That's why you can't write to it...  Therefore, you need to format it to whatever filesystem you want and then mount it somewhere before you can access it,

mke2fs -j /dev/hdb1
mkdir /mnt/second
mount -t ext3 /dev/hdb1 /mnt/second

---

### Post by SeanCallan on 2005-10-13
I wanted to mount it to the directory I already made, so I made that little change

sean@Doomspork:~$ sudo mount -t ext3 /dev/hdb1 /mnt/storage
sean@Doomspork:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             74684224  34517036  36373440  49% /
tmpfs                   388212         0    388212   0% /dev/shm
tmpfs                   388212     12588    375624   4% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1            288457376    131228 273673360   1% /mnt/storage

Now, how do I change the premissions? :)

Thanks so much for all your help bud!

---

### Post by piggyaugu on 2005-10-13
[QUOTE=SeanCallan]I wanted to mount it to the directory I already made, so I made that little change

sean@Doomspork:~$ sudo mount -t ext3 /dev/hdb1 /mnt/storage
sean@Doomspork:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             74684224  34517036  36373440  49% /
tmpfs                   388212         0    388212   0% /dev/shm
tmpfs                   388212     12588    375624   4% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1            288457376    131228 273673360   1% /mnt/storage

Now, how do I change the premissions? :)

Thanks so much for all your help bud![/QUOTE]



remount using **umask** parameter

---

### Post by SeanCallan on 2005-10-13
so something like:

sudo remount -t ext3 /dev/hdb1 /mnt/storage unmask ?

I'm new to linux, you gotta bear with me for now :| sorry

---

### Post by piggyaugu on 2005-10-13
[QUOTE=SeanCallan]so something like:

sudo remount -t ext3 /dev/hdb1 /mnt/storage unmask ?

I'm new to linux, you gotta bear with me for now :| sorry[/QUOTE]

hehe:p 

I'm a greenhand too.

You should try these:

```
% umount /dev/hdb1
```       ///or you can "umount /mnt/storage", same thing
```
% mount /dev/hdb1 /mnt/storage -o umask=0
```   ///with that umask=0, every user can access the partition. so be careful if you need extra security

---

### Post by gregor171 on 2005-11-09
Hi

I'm also a newbe to linux systems and I have a similar problem. I was working in /etc files as comp froze and I restarted sys.

can't run the system since:
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1

I tried all sorts of mount and remount commands and I always get to the point when root can't be loaded because of some "corrupted orphan". One of the options is of course reinstalling of the sys, but there goes also all updates, iptables, dns, dhcp thc services with it.

Can someone help me :( 

Greg

---

