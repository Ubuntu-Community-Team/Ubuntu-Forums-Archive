---
title: "Need help with ROOT user login."
date: 2006-07-25
forum: Desktop Environments
---

### Post by elfshadow14 on 2006-07-25
When I try to login as the su it will not let me.Does anyone know how to make it work?To be more clear it says this 

su: Authentication failure
Sorry.

---

### Post by Lord Illidan on 2006-07-25
Root user is by default disabled in Ubuntu. It is bad for security. If you need to do something which requires root priveleges, use sudo for terminal apps, and gksudo for graphical apps.

```
sudo vi /etc/X11/xorg.conf
``` will open the file with root priveleges, and ```
gksudo gedit /etc/X11/xorg.conf
``` will open gedit with root priveleges.

When you run sudo or gksudo just enter your own password.

---

### Post by elfshadow14 on 2006-07-25
Well I need to shut down the Xserver so I can install NvidiaDrivers.

---

### Post by Lord Illidan on 2006-07-25
No problem.

```
sudo /etc/init.d/gdm stop 
``` if you are running GNOME.
or ```
sudo /etc/init.d/kdm stop
``` if you are running KDE.

Then run the installer with sudo too.

Or else, enable the apt-get repos, and do a quick:

```
sudo apt-get install nvidia-glx
```

EDIT : The /etc/apt/sources.list should look like this, open it with gksudo gedit,

```
deb file:/var/cache/apt-build/repository apt-build main

#deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
# or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by 3rdalbum on 2006-07-25
If you want an actual root shell (when running a program "in place" you need it), you should type:

```
sudo su
```

---

### Post by jordilin on 2006-07-25
to enable the root account:
```
sudo passwd root
```
to disable the root account:
```
sudo passwd -l root
```
If you want temporarily a root console, then type
```
sudo -i
```
More info in:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ardchoille on 2006-07-25
It's never a good idea to enable the root account. I have been using Linux for 5+ years and have never needed to actually log in as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jordilin on 2006-07-25
> **ardchoille said:**
> It's never a good idea to enable the root account. I have been using Linux for 5+ years and have never needed to actually log in as root.

Well, it depends. What happens if you have a directory owned by root with 700 permissions (rwx------). If so, you will not be able to enter that directory with cd by typiing sudo cd directoryname.
Just see the following thread: 
[http://ubuntuforums.org/showthread.php?t=193747&highlight=sudo+cd](http://ubuntuforums.org/showthread.php?t=193747&highlight=sudo+cd)
Currently, If I need a root console I just type 
```
sudo -i
```
and I have momentarily root access.

---

### Post by jordilin on 2006-07-25
Apart from my last post, you will almost always only need sudo.

---

### Post by ardchoille on 2006-07-25
> **jordilin said:**
> Well, it depends. What happens if you have a directory owned by root with 700 permissions (rwx------). If so, you will not be able to enter that directory with cd by typiing sudo cd directoryname.
Just see the following thread: 
[http://ubuntuforums.org/showthread.php?t=193747&highlight=sudo+cd](http://ubuntuforums.org/showthread.php?t=193747&highlight=sudo+cd)
Currently, If I need a root console I just type 
```
sudo -i
```
and I have momentarily root access.

In the years that I have used Linux, I've never needed to cd into a dir that is drwx------ and owned by root. Why would one need to do that? Ninety-nine percent of the time I never even leave my ~ dir.

---

### Post by jordilin on 2006-07-25
> **ardchoille said:**
> In the years that I have used Linux, I've never needed to cd into a dir that is drwx------ and owned by root. Why would one need to do that? Ninety-nine percent of the time I never even leave my ~ dir.

You are right, but there are very specific situations that you need being the root user (very specific admin things). Apart from that, always use sudo, that's my recommendation. :-D

---

