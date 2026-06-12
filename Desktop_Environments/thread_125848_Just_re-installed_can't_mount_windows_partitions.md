---
title: "Just re-installed can't mount windows partitions"
date: 2006-02-05
forum: Desktop Environments
---

### Post by catalytic on 2006-02-05
I just re-installed, I am in my user account, I do not want a root account. Last time the only way I could access my windows files was if I was permenantly logged into my root account.

I have tried mounting the partitions as written in the starter guide, this is what I get
username@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
username@ubuntu:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1

This was one of the original problems I had that I really want to fix this time. I do not want to have to use the terminal everytime I want to grab a file. 
Please help me sort this out once and for all. This is the last time I am going to bother with Ubuntu, I'm giving it one more go...hopefully I will have better luck this time.

---

### Post by catalytic on 2006-02-05
This time I can't even view the contents in nautilus. According to properties my windows partitions are unreadable.

---

### Post by catalytic on 2006-02-05
This is the list of apparently mounted devices

/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hda5 on /media/hda5 type ntfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

### Post by Herman on 2006-02-05
>  /dev/hda6 on / type ext3 (rw,errors=remount-ro)G'day, catalytic, that up there wouldn't have anything to do with it would it? Maybe try a ```
sudo touch /forcefsck
``` and a reboot and see what happens. :D (Herman)
Edit; watch carefully during the reboot for it to do the filesystem check (equivalent to scandisk in Windows), if there are errors it will print them out at you.  You should take note of what happens at least roughly anyway. Hopefully it will fix itself automatically.

---

### Post by vruum on 2006-02-05
maybe I'm missing something, but if hda1 is your windows partition, the problem is that it's already mounted. Try ```
sudo umount /mnt/hda1
``` and then try mounting it again.

---

### Post by catalytic on 2006-02-06
Yeah thanks guys, I tried all that no success. Now it won't let me re-install again without formatting my whole hard drive.

I am now forced to run the live CD just so I can have internet access and check my email. Problem is an important wav file I need to listen to wont play!!

So that ends my foray into the world of Linux, Ubuntu has put me off using it for good. I'm sorry but windows is far less complicated and better for me.

---

### Post by aysiu on 2006-02-06
If that's the sort of thing that frustrates you, consider using Mepis. Without doing anything (just boot up, basically), all partitions and hard drives are on the desktop. You just click on any partition and it mounts and opens.

No special commands. Nothing difficult.

---

