---
title: "Impossible to start X"
date: 2007-02-04
forum: Desktop Environments
---

### Post by souraka on 2007-02-04
Hi sincce 2 days it is impossible toacces to my KUBUNTU . when i put my password i have the error message: " warning: impossible to write on /tmp, x may shut down with an error.

i try several things and what i understand now is that i have to purge my tmp directory.

i need help for that and acces again to my system
thanks

---

### Post by taurus on 2007-02-04
Boot into recovery mode from GRUB menu and past the output of these two commands here.

```
df -h
ls -la /
```

---

### Post by souraka on 2007-02-04
ok so:
df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             2.9G  2.3G  475M  84% /
varrun                506M   16K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda5              26G  2.0G   23G   8% /home
/dev/sda1              56G   34G   23G  60% /media/sda1
/dev/sda2              25G   14G   12G  53% /media/sda2



ls -la/ :

total 164
drwxr-xr-x 12 root root  4096 Feb  4 17:36 .
drwxr-xr-x 21 root root  4096 Jan 13 00:34 ..
lrwxrwxrwx  1 root root    35 Feb  4 17:35 .DCOPserver_souraka-laptop_:0 -> /root/.DCOPserver_souraka-laptop__0
-rw-r--r--  1 root root    61 Feb  4 17:35 .DCOPserver_souraka-laptop__0
-rw-------  1 root root  2259 Feb  4 17:35 .ICEauthority
-rw-------  1 root root   108 Feb  4 17:35 .Xauthority
-rw-r--r--  1 root root  2227 Jun 30  2006 .bashrc
-rw-r--r--  1 root root 31651 Jan 12 22:40 .fonts.cache-1
drwx------  2 root root  4096 Feb  4 17:36 .gconf
drwx------  2 root root  4096 Feb  4 17:37 .gconfd
drwx------  3 root root  4096 Feb  4 17:36 .gnome2
drwx------  2 root root  4096 Feb  4 17:36 .gnome2_private
-rw-r--r--  1 root root 24788 Feb  4 17:36 .gtk_qt_engine_rc
-rw-r--r--  1 root root   287 Feb  4 17:24 .gtkrc-2.0
drwx------  4 root root  4096 Feb  4 17:24 .kde
drwx------  3 root root  4096 Feb  4 17:24 .local
drwxr-xr-x  3 root root  4096 Jan 12 17:18 .mcop
-rw-------  1 root root    31 Jan 29 10:42 .mcoprc
drwx------  3 root root  4096 Feb  4 17:36 .mozilla
-rw-r--r--  1 root root   141 Jun 30  2006 .profile
drwxr-xr-x  2 root root  4096 Jan 12 16:40 .qt
-rw-------  1 root root   118 Feb  4 17:35 .serverauth.3843
-rw-------  1 root root 23661 Feb  4 17:45 .xsession-errors
drwx------  2 root root  4096 Feb  4 17:24 Desktop


hope it can help

---

### Post by taurus on 2007-02-04
Doesn't look like you have a lot of space left on /, 475MB.  And by the way, there should be a space between a and / in

```
ls -la     /
```
Try to clean out your cache with

```
sudo aptitude clean
df -h
ls -la  /
```

---

### Post by souraka on 2007-02-04
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             2.9G  2.3G  472M  84% /
varrun                506M   16K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda5              26G  2.0G   23G   8% /home
/dev/sda1              56G   34G   23G  60% /media/sda1
/dev/sda2              25G   14G   12G  53% /media/sda2



ls -la /
total 120
drwxr-xr-x  21 root root  4096 Jan 13 00:34 .
drwxr-xr-x  21 root root  4096 Jan 13 00:34 ..
lrwxrwxrwx   1 root root    41 Jan 12 17:27 .hidden -> /etc/kubuntu-default-settings/hidden-root
drwxr-xr-x   2 root root  4096 Jan 14 17:58 bin
drwxr-xr-x   3 root root  4096 Jan 12 18:50 boot
lrwxrwxrwx   1 root root    11 Jan 12 17:26 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13240 Feb  4 18:38 dev
drwxr-xr-x 109 root root  4096 Feb  4 18:39 etc
drwxr-xr-x   4 root root  4096 Jan 12 17:36 home
drwxr-xr-x   2 root root  4096 Oct 25 16:03 initrd
lrwxrwxrwx   1 root root    33 Jan 12 17:37 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  17 root root  8192 Jan 30 07:44 lib
drwxr-xr-x   2 root root 49152 Jan 12 17:25 lost+found
drwxr-xr-x   5 root root  4096 Feb  1 18:14 media
drwxr-xr-x   2 root root  4096 Oct 20 00:49 mnt
drwxr-xr-x   2 root root  4096 Oct 25 16:03 opt
dr-xr-xr-x  93 root root     0 Feb  4  2007 proc
drwxr-xr-x 15 root root  4096 Feb  4 18:47 root
drwxr-xr-x   2 root root  4096 Jan 30 07:44 sbin
drwxr-xr-x   2 root root  4096 Oct 25 16:03 srv
drwxr-xr-x  11 root root     0 Feb  4  2007 sys
drwxrwxrwt   9 root root  4096 Feb  4 18:48 tmp
drwxr-xr-x  13 root root  4096 Jan 13 00:34 usr
drwxr-xr-x  14 root root  4096 Jan 13 00:33 var
lrwxrwxrwx   1 root root    30 Jan 12 17:37 vmlinuz -> boot/vmlinuz-2.6.17-10-generic

---

### Post by taurus on 2007-02-04
So "**aptitude clean**" didn't free up any space at all!  I think the reason you can't log in right now because / is running low on space.  It needs to write to /tmp but you only have less than 0.5GB left.

What if you delete items in the trash can in root's directory.

```
rm /root/.Trash/*
```

---

### Post by souraka on 2007-02-04
root@souraka-laptop:~# rm /root/.Trash/*
rm: cannot remove `/root/.Trash/*': No such file or directory

strange no??

---

### Post by taurus on 2007-02-04
> **souraka said:**
> root@souraka-laptop:~# rm /root/.Trash/*
rm: cannot remove `/root/.Trash/*': No such file or directory

strange no??

Not really.  It just meant that there was nothing in the trash bin for root.  I guess making / only 3GB while /home with 28GB was not such a good idea at all because you are running out of space on /.  Usually, Gnome would take up almost 2.5GB so if you install other apps, then 3GB would be gone real quick.  Again, you did run this command from a prompt, right!

```
aptitude clean
```

---

### Post by souraka on 2007-02-04
ok i did it again nothing change same result 

what should i do ?

---

### Post by taurus on 2007-02-04
Probably time to start removing some apps that you don't use to free up some space so a user can log in.  Also, look in /var/log and remove those _backup_ log files, usually end with a number, .gz, or .tar.gz.

---

### Post by souraka on 2007-02-04
thanks for your help i undesrtand more things now
do you think that if i use gparted to reconfigure it could be better and i wont have this problem again? what the better size for /  for me?

---

### Post by taurus on 2007-02-04
10GB for / would give you some space to install other apps.  And of course, the more space you can have for /, the less likely you would fill it up.

---

### Post by Samhain II on 2007-02-05
Running out of space on root is not so good.  But that is not your problem here.  X does not start at all.  This would not be caused because you are running out of space.  It would only be caused if you are out of space.

Take a look at /var/log /Xorg.0.log

That should likely show the problem.  Also look at /var/log/messages and /var/log/syslog.

---

### Post by souraka on 2007-02-06
> **Samhain II said:**
> Running out of space on root is not so good.  But that is not your problem here.  X does not start at all.  This would not be caused because you are running out of space.  It would only be caused if you are out of space.

Take a look at /var/log /Xorg.0.log

That should likely show the problem.  Also look at /var/log/messages and /var/log/syslog.

Hi Samhain i just see your post. i look at those files but it is like chinese for me :confused: 

what informations should i find in it?

---

### Post by Highjo on 2007-02-06
I 'm new to linux.I'm supposed to use RedHat or Fedora but ubuntu is the one i can i install.I find it cool even though i don't know much yet about it.
Since we are talking about X.Im having the same problem but it is after mounting manipulations.I thing i did something wrong.I can only boot in CUI and it seems even with sudo command i can't change anything.

After logging in CUI i typed startx what it's showed is in txt format attached

---

### Post by dagnabit dang doohickey on 2007-02-06
If freeing up space is the issue, you might be able to squeeze out some more by cleaning your thumbnails cache. The ~/.thumbnails directory can grow pretty big after awhile.

```
find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```


[edit: I spoke to soon. This tip would come in handy for a user of Gnome, but probably not for KDE.]

---

