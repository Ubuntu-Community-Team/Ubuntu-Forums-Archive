---
title: "Mount Disc"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Natsuki on 2005-11-22
[FONT="Trebuchet MS"][SIZE="2"]I'm kinda new with this

What can i do to do not have to mount my partition every time my ubuntu start.

I do this all the time:
> mkdir /mnt/win
sudo mount -t vfat /dev/hda4 /mnt/win

I try this for write/read permission but it says permission denied. I'm using the root user.

> /dev/hda4 /mnt/win vfat rw,*user*   0 0

Beside that i use the same to try to mount my others partitions and doesnt work.

> mkdir /mnt/wind
sudo mount -t vfat /dev/hdb1 /mnt/wind

Ps. I know that this issues is more that burned. I was searching but i really didn't find out some useful.

Bye
Thanks :oops: [/SIZE][/FONT]

---

### Post by alvonsius on 2005-11-22
[QUOTE=Natsuki][FONT="Trebuchet MS"][SIZE="2"]I'm kinda new with this

What can **i do to do not have to** mount my partition every time my ubuntu start.

 [/SIZE][/FONT][/QUOTE]

So ... do you want to do or do you want not :D hehe just joke

Humm, I never did this before, since when I first install Kubuntu I set it to mount every partition I have. But in this case, maybe :

- Create a directory with root account where you want to mount your partition and set it  to 777 or 755
- Set your /etc/fstab file like mine here :

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /download       ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6       /music          ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

- Restart your machine ... and check the directory you've created ... For more information visit the fstab manpage or webpage.

Hope it help ... :D

---

### Post by Natsuki on 2005-11-27
Thanks i'll try that ;)

---

