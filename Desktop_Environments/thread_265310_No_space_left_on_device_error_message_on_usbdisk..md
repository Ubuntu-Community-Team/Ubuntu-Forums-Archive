---
title: "No space left on device error message on usbdisk."
date: 2006-09-25
forum: Desktop Environments
---

### Post by mihailis on 2006-09-25
I've run into a little problem with Ubuntu and my 300Gb Maxtor USB hard drive.  Everything was working fine earlier, but now I'm getting a "No space left on device" message when I try to move files onto it--this happens both with Gnome's file manager and a terminal.  I have deleted the files in the .Trash directory and df shows that there is space left on the drive.

root@chachazero:/media/usbdisk# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              49G  4.6G   42G  10% /
varrun                760M   84K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M  156K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   19M  742M   3% /lib/modules/2.6.15-27-386/volatile
/dev/sda1             280G  192G   88G  69% /media/usbdisk

I've even run 'cat /dev/zero >> Testfile' in the /media/usbdisk directory and it happily creates the file and begins adding to it.

Here's the output line for the usbdisk when running mount:

/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

Anyone have any recommendations?

---

### Post by orb9220 on 2006-09-25
> /dev/sda1 on /media/usbdisk type vfat [COLOR="Red"]([/COLOR]rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gi d=1000,umask=077,iocharset=utf

Is there a ( in your fstab? Never seen one of those in an fstab before.

---

### Post by mihailis on 2006-09-25
I don't have an entry for the usbdisk in the fstab, it detects automatically when I connect it.  The line is from when I run the 'mount' command by itself.  Also that last part should read "(utf8 )" without the space.  The board converted that into a smiley.

---

