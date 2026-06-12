---
title: "Sources list Error"
date: 2009-06-22
forum: General Help
---

### Post by Josh G on 2009-06-22
I'm new to Ubuntu and I messed up the sources list and don't know how to fix it.

I was following [**this**](http://www.unixmen.com/linux-distributions/ubuntu/265-great-themes-for-ubuntu-904-jaunty-jackalope) tutorial trying to add themes to Ubuntu. I did the first part and added these two lines to the end of the sources list.
> 
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
Now when I try to update the cache using *sudo apt-get update* but now I get an error.
> 
E: Type 'Jaunty Jackalope' is not known on line 55 in source list /etc/apt/sources.list

I also can't add/remove applications because of this.

Anyone know how I can fix this?

---

### Post by kostkon on 2009-06-22
Could you post your sources list here? To do it, open a terminal (Applications &#8594; Accessories &#8594; Terminal) and give
```
gedit /etc/apt/sources.list
```
and paste the contents of the file here.

---

### Post by Josh G on 2009-06-22
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04
"Jaunty Jackalope"
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main                      

```

---

### Post by CatKiller on 2009-06-22
> **Josh G said:**
> ```
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04
"Jaunty Jackalope"

```

This bit is the problem. The Wine description has run over two lines. You can run ```
gksudo gedit /etc/apt/sources.list
``` to correct it.

---

### Post by Josh G on 2009-06-22
I ran that in Terminal and it opens the sources.list file but it is still the same. Do I have to edit the file again?

Like I said I'm new to Ubuntu and I don't really know much about it yet. :neutral:

---

### Post by SuperSonic4 on 2009-06-22
You may also comment out the "Jaunty Jackalope" line by putting a # infront of it:

#"Jaunty Jackalope"

---

### Post by Josh G on 2009-06-22
> **SuperSonic4 said:**
> You may also comment out the "Jaunty Jackalope" line by putting a # infront of it:

#"Jaunty Jackalope"

Thanks! That worked perfect.

---

### Post by CatKiller on 2009-06-22
> **Josh G said:**
> I ran that in Terminal and it opens the sources.list file but it is still the same. Do I have to edit the file again?

Yes :) To correct the fact that one line has been split over two, and the system has absolutely no idea what it's supposed to do with the second half of that line, since it's a comment for a human reader.

---

### Post by SuperSonic4 on 2009-06-23
> **Josh G said:**
> Thanks! That worked perfect.

Just as a background the comment tells the computer to ignore what's coming after it and it does the same thing in nearly every script file.

---

