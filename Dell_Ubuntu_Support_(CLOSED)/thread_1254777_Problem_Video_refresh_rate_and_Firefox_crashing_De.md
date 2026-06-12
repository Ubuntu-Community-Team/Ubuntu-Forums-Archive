---
title: "Problem Video refresh rate and Firefox crashing Dell Inpiron Mini 10"
date: 2009-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lindylex on 2009-08-31
I have a Dell Inpiron Mini 10

I am trying to install Ubuntu Jaunty and I have the following problems.

[ONE]
The video refresh rate is slow.  

This is the video car

lspci | grep VGA

```

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

```

/etc/X11/xorg.conf

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


```

[TWO]
Firefox 3.0.13 and mplayer plugins crashes the browser when I try to view a movie trailer at Apple's website

/etc/apt/sources.list

```

#deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu jaunty partner
 deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse


```

uname -a 

```

Linux 2.6.28-15-generic #49-Ubuntu SMP i686 GNU/Linux

```

---

### Post by lindylex on 2009-09-01
Solution for the video.


1. create the file /etc/apt/sources.list.d/ubuntu-mobile.list
2. sudo vi /etc/apt/sources.list.d/ubuntu-mobile.list
3. add the following content to the newly created file:
	deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
	deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
4. sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys C6598A30
5. sudo apt-get update
6. sudo aptitude install psb-kernel-source psb-kernel-headers
7. sudo reboot
8. sudo aptitude install xserver-xorg-video-psb
9. sudo reboot

You /etc/X11/xorg.conf file will look like this.

```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "AccelMethod" "EXA"
	Option 		"DRI" "off"
        Option          "MigrationHeuristic" "greedy"
	Option 		"IgnoreACPI" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



```

[VERY IMPORTANT EDIT 2009.October]

If you upgrade your kernel you have to rebuild this &#8220;psb-kernel-sourc&#8221; source by doing the following.

sudo dpkg-reconfigure psb-kernel-source

After rebooting the 1366×768 resolution should be working on Dell Inspiron mini 10 running Ubuntu Jaunty

---

