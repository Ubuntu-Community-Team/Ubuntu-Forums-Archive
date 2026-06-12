---
title: "Trash shows root filesystem"
date: 2007-06-04
forum: Desktop Environments
---

### Post by pablo13 on 2007-06-04
Hi all, 

I'm having a very strange problem ... The gnome Trash shows the deleted items as well as all the root filesystem ... and when I clicked on the "Empty Trahs" button it tried to erase the actual "/" filesystem :( :( Luckily I did'nt have permission so It gave me an error ... 

I have written a file /test.txt and It appears on the Trash .. so don't know why but the trash is geting both the files in the real trash and also the files and dirs in "/" 

I have taken a screenshot where you can see the whole "/" and also a file I actually deleted called "localhost.sql" ....

[http://img376.imageshack.us/img376/5240/erroruv9.jpg](http://img376.imageshack.us/img376/5240/erroruv9.jpg)

Any clue why is this happening ¿?¿?

Thanks,
Pablo

---

### Post by tgalati4 on 2007-06-04
Whatever you do, don't reboot.  Linux will keep running but if you reboot, you may never get back into your system.

Normally things only get put in the Trash through the file manager Nautilus using right-click, "Move to Trash".

To restore an item, you drag it back to where it belongs.  As a non-root user, this won't work with the root directory.

Now would be a good time to back up your /home/pablo directory.  You may need to reinstall if you are not successful in restoring root.

Open a terminal (Alt-F2):

Report the output of the following:

cd /
ls -la
sudo su
cd /
ls -la

---

### Post by pablo13 on 2007-06-05
Hi, I've already rebooted the system and everything went ok ... But the trash can still shows the / on it ....

Here's the output ... nothing relevant I think.

Btw, I placed a new file named "kk" on the / and It directly appeared on the Trash ... wtf this is very strange !!!

Thks for the reply!
Pablo

[ptoharia@ptoharia[0](10:23am)/]>ls -al
total 152
drwxr-xr-x  24 root root  4096 2007-06-04 16:21 .
drwxr-xr-x  24 root root  4096 2007-06-04 16:21 ..
drwxr-xr-x   3 root root  4096 2006-01-26 19:33 backup
drwxr-xr-x   2 root root  4096 2007-05-08 11:39 bin
drwxr-xr-x   3 root root  4096 2007-05-29 11:35 boot
lrwxrwxrwx   1 root root    11 2005-11-10 15:11 cdrom -> media/cdrom
drwxr-xr-x   2 root root  4096 2005-11-10 15:14 debootstrap
drwxr-xr-x  15 root root 14280 2007-06-04 10:36 dev
drwxr-xr-x 157 root root  8192 2007-06-04 10:41 etc
-rw-r--r--   1 root root  4382 2006-03-06 10:10 hdparm.conf
drwxr-xr-x   9 root root  4096 2006-03-16 14:40 home
drwxr-xr-x   2 root root  4096 2005-11-10 15:12 initrd
lrwxrwxrwx   1 root root    33 2007-05-29 11:36 initrd.img -> boot/initrd.img-2.
6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-05-08 12:13 initrd.img.old -> boot/initrd.im
g-2.6.20-15-generic
-rw-r--r--   1 root root     0 2007-06-04 16:21 kk
drwxr-xr-x  21 root root  8192 2007-05-08 12:32 lib
drwxr-xr-x   2 root root 49152 2005-11-10 15:10 lost+found
drwxr-xr-x   8 root root  4096 2007-06-04 10:35 media
drwxr-xr-x   2 root root  4096 2005-10-05 11:37 mnt
drwxr-xr-x   2 root root  4096 2005-11-16 14:59 old
drwxr-xr-x   8 root root  4096 2007-05-25 16:12 opt
dr-xr-xr-x 182 root root     0 2007-06-04 12:35 proc
drwxr-xr-x  28 root root  4096 2007-06-01 17:22 root
drwxr-xr-x   2 root root  8192 2007-05-29 11:35 sbin
drwxr-xr-x   2 root root  4096 2005-11-10 15:12 srv
drwxr-xr-x  11 root root     0 2007-06-04 12:35 sys
drwxrwxrwt  19 root root  8192 2007-06-05 10:16 tmp
drwxr-xr-x  16 root root  4096 2007-05-08 16:56 usr
drwxr-xr-x  16 root root  4096 2007-01-12 17:08 var
lrwxrwxrwx   1 root root    30 2007-05-29 11:36 vmlinuz -> boot/vmlinuz-2.6.20-1
6-generic
lrwxrwxrwx   1 root root    30 2007-05-08 12:13 vmlinuz.old -> boot/vmlinuz-2.6.
20-15-generic
[ptoharia@ptoharia[0](10:23am)/]>sudo su
Password:

root@ptoharia:/#
root@ptoharia:/# cd /
root@ptoharia:/# ls -la
total 152
drwxr-xr-x  24 root root  4096 2007-06-04 16:21 .
drwxr-xr-x  24 root root  4096 2007-06-04 16:21 ..
drwxr-xr-x   3 root root  4096 2006-01-26 19:33 backup
drwxr-xr-x   2 root root  4096 2007-05-08 11:39 bin
drwxr-xr-x   3 root root  4096 2007-05-29 11:35 boot
lrwxrwxrwx   1 root root    11 2005-11-10 15:11 cdrom -> media/cdrom
drwxr-xr-x   2 root root  4096 2005-11-10 15:14 debootstrap
drwxr-xr-x  15 root root 14280 2007-06-04 10:36 dev
drwxr-xr-x 157 root root  8192 2007-06-04 10:41 etc
-rw-r--r--   1 root root  4382 2006-03-06 10:10 hdparm.conf
drwxr-xr-x   9 root root  4096 2006-03-16 14:40 home
drwxr-xr-x   2 root root  4096 2005-11-10 15:12 initrd
lrwxrwxrwx   1 root root    33 2007-05-29 11:36 initrd.img -> boot/initrd.img-2.
6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-05-08 12:13 initrd.img.old -> boot/initrd.im
g-2.6.20-15-generic
-rw-r--r--   1 root root     0 2007-06-04 16:21 kk
drwxr-xr-x  21 root root  8192 2007-05-08 12:32 lib
drwxr-xr-x   2 root root 49152 2005-11-10 15:10 lost+found
drwxr-xr-x   8 root root  4096 2007-06-04 10:35 media
drwxr-xr-x   2 root root  4096 2005-10-05 11:37 mnt
drwxr-xr-x   2 root root  4096 2005-11-16 14:59 old
drwxr-xr-x   8 root root  4096 2007-05-25 16:12 opt
dr-xr-xr-x 184 root root     0 2007-06-04 12:35 proc
drwxr-xr-x  28 root root  4096 2007-06-01 17:22 root
drwxr-xr-x   2 root root  8192 2007-05-29 11:35 sbin
drwxr-xr-x   2 root root  4096 2005-11-10 15:12 srv
drwxr-xr-x  11 root root     0 2007-06-04 12:35 sys
drwxrwxrwt  19 root root  8192 2007-06-05 10:16 tmp
drwxr-xr-x  16 root root  4096 2007-05-08 16:56 usr
drwxr-xr-x  16 root root  4096 2007-01-12 17:08 var
lrwxrwxrwx   1 root root    30 2007-05-29 11:36 vmlinuz -> boot/vmlinuz-2.6.20-1
6-generic
lrwxrwxrwx   1 root root    30 2007-05-08 12:13 vmlinuz.old -> boot/vmlinuz-2.6.
20-15-generic
root@ptoharia:/#

---

### Post by tgalati4 on 2007-06-06
Others are experiencing this problem as well, so it may be a Feisty update issue.  Backup your work and watch the boards.

---

### Post by pablo13 on 2007-06-12
I found a solution.

I erased .gnome/gnome-vfs/.trash-cache (or something like that) and rebooted. Now the trash shows the correct files. But now the gnome trash applet shows always an empty trash ... while the desktop icon works fine.

Cheers
Pablo

---

