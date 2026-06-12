---
title: "Different filenames on my computers"
date: 2006-09-11
forum: Desktop Environments
---

### Post by HakanS on 2006-09-11
Yesterday I installed Kubuntu Dapper on my laptop.
I already have a PC with Kubuntu Dapper and to be able to share files between them I installed OpenSSH on both.
When I transfered some files with swedish characters (å,ä,ö) in the filename from the PC to the laptop the filenames don´t have the swedish characters when I listed them in the laptop.
I think I have UTF-8 on both machines. How can i check it?

---

### Post by lukew on 2006-09-11
what filesystem types are they?

you can perform mount without any paremters to list the mount points and how they are mounted.

Luke

---

### Post by HakanS on 2006-09-11
The desktop PC is Reiserfs and the laptop is ext3.
I will check with mount.
I checked with locales yesterday and got the same results from both machines.

---

### Post by HakanS on 2006-09-11
Mount on the desktop PC gives the result:
```
/dev/hda5 on / type reiserfs (rw,noatime,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext2 (rw,noatime)
/dev/hda6 on /usr type reiserfs (rw,noatime)
/dev/hda8 on /var type reiserfs (rw,noatime)
/dev/hda9 on /home type reiserfs (rw,noatime)

```
Mount on the laptop gives the result:
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)

```
Is it OK?

---

### Post by HakanS on 2006-09-14
Solved
It´s a bug in the fish kioslave. It can´t handle unicode filenames.

---

