---
title: "Help! An Install mistake."
date: 2006-06-20
forum: Desktop Environments
---

### Post by linux-nOOb on 2006-06-20
I just completed a reinstall of Dapper and in my haste I forgot to mount home on my /home partiton.](*,)  Can one of you gurus tell me if there is a way to mount it without reinstalling again? I know that it can probably be linked but I would rather have it mounted where it is supposed to be.

Thank you in advance for your time.

nOOb

---

### Post by taurus on 2006-06-20
Boot into recovery mode.  At the prompt, edit /etc/fstab
```

nano /etc/fstab

```
and add this line at the end of it...
```

/dev/hda3       /home           ext3    defaults        0       2
(assuming that /dev/hda3 is your home partition and you use ext3 filesystem...)

```
Save it and reboot as normal!

---

### Post by lamego on 2006-06-20
First you need to know what is the partitiona name of your previous /home.
To list all your partitions:
```
 sudo fdisk -l
```
Then just edit an entry for it:
  sudo gedit /etc/fstab

Reboot the system to make sure the current /home will be unmounted and the old part will be mounted.

---

### Post by linux-nOOb on 2006-06-20
Man you guys are fast....thanks for your time.:)

Here is my /etc/fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc5       /media/hdc5     ntfs    defaults        0       0
/dev/hdc6       /media/hdc6     ntfs    defaults        0       0
/dev/hdc7       /media/hdc7     ntfs    defaults        0       0
/dev/hdc8       /media/hdc8     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

``` 
So I should just change /media/sda6 to /home/sda6?

Thanks again for your help,
nOOb

---

### Post by Dakaru on 2006-06-20
Holy hell. That Fstab is huge.

---

### Post by linux-nOOb on 2006-06-20
LOL@Dakaru:lol:

Yes it is....but can you tell me if changing /media/sda6 to /home/sda6 will infact mount my home file on my /home partiton?

Thanks for the help,
nOOb

---

### Post by taurus on 2006-06-20
Look at my reply up there!!!  Replace the /dev/hda3 with /dev/sda6...  :roll:

---

### Post by linux-nOOb on 2006-06-20
Thanks taurus,

I see you rolling your eyes but I just wanted clarafication before I f**ked anything up....again!

Thanks for your time...this is what brought me to Ubuntu....the great community.
On many forums I would have gotten a RTFM response...your the Man.

Thanks again for your time, you have just saved me a bunch,
nOOb

---

