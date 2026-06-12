---
title: "Icons in gnome menu"
date: 2010-03-22
forum: Desktop Environments
---

### Post by chobong on 2010-03-22
Dear All,

I have installed Ubuntu 9.10 and want to change Ubuntu looks like windows7.
So, I installed gnome-menu 1.9 and change it to windows7's menu , it's ok. 
But when I click at Gnome-menu, there is no any icons for applications (at left). 
How can I get icons for my menu?
Please help me. Thank so much!

---

### Post by dusdus on 2010-03-22
You mean you installed GnoMenu 1.9 ([http://ubuntu.hamdi.web.id/other-stuff/gnomenu-19-consolidated-menu-for-gnome.html)?](http://ubuntu.hamdi.web.id/other-stuff/gnomenu-19-consolidated-menu-for-gnome.html)?)

And how did you install it? Using the .deb-file or adding the PPA to your sources.list?

Personally I would install it by typing in the terminal
```

sudo add-apt-repository ppa:gnomenu-team/ppa
[code]

After that, type from termimal
[code]
gksudo gedit /etc/apt/sources.list

```

and add this line to the end of the file
```

deb http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu 

```

the run from terminal
```

sudo apt-get update && sudo apt-get install gnomenu

```

I guess :D

---

### Post by chobong on 2010-03-22
I installed gnome-menu with source.
This is the link [https://launchpad.net/gnomenu/trunk/1.9](https://launchpad.net/gnomenu/trunk/1.9) 
and after run the command
# sudo make install

I don't know how to remove this package also, even i run # sudo make uninstall, but it wasnot uninstall, just missed icons. 

Now i don't know how to do :(

---

### Post by dusdus on 2010-03-22
I guess you did
```

./configure
make
sudo make install

```

right?

Make sure you are in the right directory when you use "sudo make uninstall"

And try to follow my instructions in my first reply

---

### Post by chobong on 2010-03-22
I run this command
```

sudo apt-get update && sudo apt-get install gnomenu

```

And it showed 
E: Malformed line 49 in source list /etc/apt/sources.list (dist)

How should I do ? :(

---

### Post by dusdus on 2010-03-22
How does your /etc/apt/sources.list look like?
Show us :)

---

### Post by chobong on 2010-03-22
This is my source.list 

> 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu)


---

### Post by dusdus on 2010-03-22
oops

please add
```

karmic main

``` 
at the end of the line, my bad

```

deb http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu karmic main

```

and then sudo apt-get update && sudo apt-get install gnomenu

---

### Post by chobong on 2010-03-22
Thank you so much, dusdus :)

It's working :guitar:

---

### Post by dusdus on 2010-03-22
Yay! Have fun :)

Please change the status of this topic, by using "Thread tools" and select "Mark this thread as solved"

---

### Post by tanari on 2010-03-22
how to do this in 10.04?

---

