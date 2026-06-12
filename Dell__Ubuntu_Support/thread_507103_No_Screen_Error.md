---
title: "No Screen Error"
date: 2007-07-22
forum: Dell  Ubuntu Support
---

### Post by berylSCRIPT on 2007-07-22
OK, so I was updating my Ubuntu to Beryl and I was changing the source.list. 

I accidentally deleted what was in there before and now when I tried to boot up my computer it goes to a 
screen with a whole bunch of different symbols saying that there was an error booting up the X graphics thing.

No screen was found.

I can still type in commands and stuff and I just wanted to know if there was anyone else who had this problem and if they could help me fix it myself.

Thank you.

---

### Post by berylSCRIPT on 2007-07-22
THIS IS PRETTY MUCH WHAT IT SAYS

> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux admin-desktop 2.6.15-28-386 #1 PREEMPT
Wed Jul 18 22:50:32 UTC 2007 i686
              Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
              to make sure that you have the lastest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
               (++) from command line, (!!) notice, (II) informational,
               (WW) warning, (EE) error, (NI) not implemented, (??) unkown.
(==) Log file: '/var/log/Xorg.0.log", Time: Sun Jul 22 12:49:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by jimbob on 2007-07-22
Here is the earliest one of mine so that you can copy and paste it to your system.

Hope this will get you going again:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by brettr on 2007-07-23
That is a strange problem to have. The starting of X does not depend on sources.list, although if it was updating and there were a bunch of broken packages then i suppose it is possible. If using the posted sources file does not work, you might be looking at a misconfigured /etc/X11/xorg.conf file. you also might want to run an ```
sudo apt-get check
``` This should check dependencies and see if there are broken packages. Also when you change the sources.list file you have to update the package database

---

### Post by strabes on 2007-07-24
Uhhhh this is not a sources.list error. It's an /etc/X11/xorg.conf error. Run these commands in the terminal it dumps you to (the defaults should be fine for the first one): ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

