---
title: "What the hell??? The directory /home does not belong to you!"
date: 2005-04-23
forum: Desktop Environments
---

### Post by raid517 on 2005-04-23
Hi, whenever I try to run wine or several other applications that depend on access to my home directory, I always get an error saying the 

```
HOME directory (/home/myusername) does not belong to you. Please check the value of $HOME and or use su-".
```

Also when I use sudo to launch konqueror I get the following message:

```
sudo konqueror
Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/tmp/kde-root"
kdecore (KAction): WARNING: KAction::initPrivate(): trying to assign a shortcut (Alt+Plus) to an unnamed action.
kdecore (KAction): WARNING: KAction::initPrivate(): trying to assign a shortcut (Alt+Minus) to an unnamed action.
Error: "/tmp/ksocket-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
```

I have checked all of these directories, and they show up in KDE as being owned by raid517 in the users group. I have raid517 set as a member of the users group.

The question is, what on earth is going on?

GJ

---

### Post by Rodrigo on 2005-04-23
hehe, what a mess...
I have Wine too, and doesnt give me that problem... I really dont know why this happen to you.
Try changing the owner of the folder ( chown ) or change permissions chmod.

---

### Post by alastair on 2005-04-23
Type (logged in as yourself) :

id
ls -l /home
echo $HOME

---

### Post by AndersAA on 2005-04-23
you using sudo or have suid set on this?

also check if something has screwed with $USER (echo $USER) and check output of "whoami"

"Error: "/var/tmp/kdecache-raid517" is owned by uid 1002 instead of uid 0."

seems it's expecting the file to have uid 0 (root) instead of your uid (I'm guessing, 1002).

---

### Post by raid517 on 2005-04-24
```
raid517@mylinux1:~$ whoami
raid517
raid517@mylinux1:~$ echo $USER
raid517
raid517@mylinux1:~$ ls -l /home
total 4
drwxr-xr-x  21 raid517 users 4096 2005-04-24 08:01 raid517
raid517@mylinux1:~$ echo $HOME
/home/raid517
raid517@mylinux1:~$
```

So what gives?

GJ

---

### Post by AndersAA on 2005-04-24
hm... ls -l /

see if the home directory has some funky permissions.

---

### Post by raid517 on 2005-04-24
```
$ ls -l /
total 117
drwxr-xr-x    2 root root  4096 2005-04-20 05:41 bin
drwxr-xr-x    5 root root  1024 2005-04-22 11:56 boot
lrwxrwxrwx    1 root root    11 2005-04-13 08:18 cdrom -> media/cdrom
drwxrwxrwx    3 root root  4096 2005-04-17 22:40 chroot
drwxr-xr-x   14 root root 14460 2005-04-24 06:17 dev
drwxr-xr-x  135 root root  8192 2005-04-24 06:17 etc
drwxr-xr-x    3 root root  4096 2005-04-24 08:01 home
drwxr-xr-x    2 root root  4096 2005-04-13 08:20 initrd
lrwxrwxrwx    1 root root    26 2005-04-22 11:06 initrd.img -> boot/initrd.img-2                                                                           .6.11.7-1
lrwxrwxrwx    1 root root    27 2005-04-22 10:13 initrd.img.old -> boot/initrd.i                                                                           mg-2.6.11-1-k7
drwxr-xr-x   15 root root  4096 2005-04-15 01:11 lib
drwxr-xr-x    2 root root 49152 2005-04-13 08:18 lost+found
drwxr-xr-x   10 root root  4096 2005-04-20 02:06 media
drwxr-xr-x    3 root root  4096 2005-04-20 02:02 mnt
drwxr-xr-x    6 root root  4096 2005-04-23 16:40 opt
dr-xr-xr-x  120 root root     0 2005-04-24 03:47 proc
drwxr-xr-x   25 root root  4096 2005-04-24 08:03 root
drwxr-xr-x    2 root root  8192 2005-04-23 17:30 sbin
drwxr-xr-x    2 root root  4096 2005-04-13 08:20 srv
drwxr-xr-x   10 root root     0 2005-04-24 03:47 sys
drwxrwxrwt   26 root root  4096 2005-04-24 16:20 tmp
drwxr-xr-x   14 root root  4096 2005-04-22 06:14 usr
drwxr-xr-x   17 root root  4096 2005-04-23 16:40 var
lrwxrwxrwx    1 root root    23 2005-04-22 11:06 vmlinuz -> boot/vmlinuz-2.6.11.                                                                           7-1
lrwxrwxrwx    1 root root    24 2005-04-22 10:13 vmlinuz.old -> boot/vmlinuz-2.6                                                                           .11-1-k7
```

Can you tell anything unusual from this?

GJ

---

### Post by crazybill on 2005-04-24
Open a terminal

chown -R  username:usergroup /home/username

where the username:usergroup is your username and group (usually same name)
fixed

---

### Post by stengah on 2006-11-15
Note: I'm on Ubuntu (edgy eft); NOT Kubuntu. I got the same error message as I tried to install crossover office using the command "sudo sh install-crossover-standard-prerelease-6.0.0beta3.sh" - apparantly I shouln't install as superuser (sudo) in a specific user's home directory. Leaving out "sudo" did the trick - just figured this might help others...:)

---

