---
title: "Automount USB drive at startup"
date: 2009-06-17
forum: General Help
---

### Post by Rob8900 on 2009-06-17
Hi,

I want my USB drive mounted automatically at startup in /media. I use the latest version of XUbuntu.

When I go to Thunar File Manager, I see my USB drive with correct name in the left column but the USB drive is not mounted in /media.

There are now 2 cases when the drive gets mounted automatically in /media:
  - When I click on the icon of the USB drive in the left column
  - When I replug the USB drive

The settings for Removable Drives and Media are checked correctly:
  - Mount removable drives when hot-plugged
  - Mount removable media when inserted
  - Browse removable media when inserted
  - Auto-run programs on new drives and media
  - Auto-open files on new drives and media

I already tried the AutoFS Automounter, but it did not work for me.

Can anyone help, please?

Thanks in advance,

Rob

---

### Post by masux594 on 2009-06-17
Hi.. Only a question.. what is the name in the media folder of your usb device?
[for post the exact command :D]

---

### Post by sahabcse on 2009-06-17
For Mounting NTFS and FAT32 partition follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by PureLoneWolf on 2009-06-17
sudo apt-get install pysdm

That will allow you to graphically configure your attached devices and save it to fstab.

It's what I used until I got used to fstab

---

### Post by Rob8900 on 2009-06-17
> **masux594 said:**
> hi.. Only a question.. What is the name in the media folder of your usb device?
[for post the exact command :d]

"rob" ;)

---

### Post by masux594 on 2009-06-17
sorry, one more thing.. post the result of ```
df -T
``` 

Sysc, A

---

### Post by Rob8900 on 2009-06-18
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3     1880648   1626268    254380  87% /
varrun       tmpfs      111584       200    111384   1% /var/run
varlock      tmpfs      111584         0    111584   0% /var/lock
udev         tmpfs      111584        48    111536   1% /dev
devshm       tmpfs      111584         0    111584   0% /dev/shm
lrm          tmpfs      111584     38684     72900  35% /lib/modules/2.6.24-19-generic/volatile

---

### Post by masux594 on 2009-06-18
Hmm.. when you typed this command, the usb keys isn't mounted.. or i'm wrong? If wasn't mounted, mount the usb key, and after re-post the command ```
df -T
```


Sysc, A

---

