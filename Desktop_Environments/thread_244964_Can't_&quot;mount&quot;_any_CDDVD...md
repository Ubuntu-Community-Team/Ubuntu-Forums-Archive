---
title: "Can't &quot;mount&quot; any CD/DVD.."
date: 2006-08-27
forum: Desktop Environments
---

### Post by Nesousx on 2006-08-27
Hey,

I am posting here due to a weird problem.

**The problem:**

I can't acces to my DVD/CD drive, whatever the media is inside, i got the following error:

```
mount: périphérique de type bloc /dev/hdb est protégé en écriture, on le monte en lecture seulement

mount: /dev/hdb est déjà monté ou /media/cdrom est occupé

mount: selon mtab /dev/hdb est déjà monté sur /media/cdrom
```

It means that: 
[B]/dev/hdb is read protected.
/dev/hdb already mounted or /dev/hdb is busy
according to mtab /dev/hdb is already mounted on /media/cdrom[/B]

Also, when I put a CD/DVD, it doesn't mount on the desktop, but only inside Nautilus. Same stufff happens with an audio CD, but I can play it using VLC.


**My system:**

Using Dapper.

My fstab:
```
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom   udf,iso9660 user,noauto,rw     0       0
none		/proc/sys/fs/binfmt_misc	binfmt_misc	defaults
```
My mtab:
```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/sda3 /home ext3 rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdb /media/cdrom iso9660 ro,noexec,nosuid,nodev,user=nesousx,rw 0 0
```

**What I tried:**
Create a folder /media/cdrom0, and change mtab then fstab, then both accordingly.
"chmod 777" on /media/cdrom, and /media/cdrom0
Removing/adding the "rw" in the fstab file.

Also, last but not least (maybe) when entering "df" in the console, I get the following:
```

Sys. de fich.           1K-blocs       Occupé Disponible Capacité Monté sur
/dev/sda1             20644348   4980060  14615712  26% /
varrun                 1038232       104   1038128   1% /var/run
varlock                1038232         4   1038228   1% /var/lock
udev                   1038232       104   1038128   1% /dev
devshm                 1038232         0   1038232   0% /dev/shm
/dev/sda3            190726392  94154880  90758476  51% /home
df: `/media/cdrom0': Permission non accordée
```

Which means that I am not allowed to browse or seomething the CDROM.

Thanks a lot in advance.

PS: I've got the exact same problem with my "MP3 player" which used to be mounted perfectly as an external HDD. The CD drive also worked like a charm.
I can't figure out what went wrong :(

---

### Post by Nesousx on 2006-08-27
Anyone, please?

---

### Post by atomkarinca on 2006-08-27
a cheap shot :) but you may try to unmount the device first and then mount it.

sudo umount -l /media/cdrom0

---

### Post by Nesousx on 2006-08-27
The command doesn't return any error, but I still got the same error message while trying to browse the CD/DVD.

---

### Post by Nesousx on 2006-08-27
](*,)

---

### Post by Nesousx on 2006-08-27
Ok, I treid a few more stuff.

Using a terminal, and after entering the command: "su -"
I can browse inside that terminal the content of my CD drive...
Any idea?
Thanks!

---

### Post by Nesousx on 2006-08-27
Still stuck :/

---

### Post by mdecler2 on 2006-08-27
Same exact problem with mounting a CD/DVD in my drive...seems kind of useless if Ubuntu doesn't support that sort of thing.

I am very skeptical that this problem is very hard to solve. Could someon shed a little light on the subject?

---

### Post by Nesousx on 2006-08-28
bump :D

---

### Post by Nesousx on 2006-08-31
bump, again.

---

### Post by bp903 on 2006-09-08
I just upgraded to Dapper Drake and I'm having the same problem.  Any luck?


B

---

