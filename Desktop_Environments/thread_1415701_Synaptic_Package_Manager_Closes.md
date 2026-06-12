---
title: "Synaptic Package Manager Closes"
date: 2010-02-25
forum: Desktop Environments
---

### Post by Kakers on 2010-02-25
Hi there guys,

Wondering if any of you can help me with a computer I have at work, it is one that was running 8.04 but has been upgraded to 9.04. 

Whenever I try to open the Synaptic Package Manager or the Update Manager it just closes within a second, no error messages or anything :( Could anyone advise me of a possible fix or if it is corrupted in some way how to remove it and reinstall.

Thanks

---

### Post by MooPi on 2010-02-25
Open a terminal and start Synaptic in the terminal. Paste any error messages back here if it closes.
> gksu synaptic

---

### Post by Kakers on 2010-02-25
Opened up a terminal and ran 'gksu synaptic' and got the same thing, opens and then closes so fast you can't read anything, no error messages are displayed.

Thought it'd try to install via command line typing and of the following:

sudo apt-get install mysqld
sudo apt-get remove synaptic
sudo aptitude remove synaptic

I keep getting 'Segmentation faultsts... 0%' Then it goes back to the command line entry... strange...

---

### Post by MooPi on 2010-02-25
To eliminate some possibilities, try ```
sudo apt-get update
``` then  ```
sudo apt-get upgrade
``` Hopefully no errors will occur. If you get errors post the contents of this file > /etc/apt/sources.list

---

### Post by Kakers on 2010-02-25
Seems like the sources updated as it downloaded like normal but at the end it gave the 'Segmentation faultsts.. 0%' again, the same for apt-get upgrade.

Both of those were run after restoring the original (sources.list.bak) to (sources.list).

But here it is:
```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

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
```

---

### Post by MooPi on 2010-02-25
Nothing is jumping out on your list that indicates a problem. One thing is the top line is empty past the # symbol. Possibly edit that out and test ?I've noticed that the top and second lines of your souces list are missing. Go to System/Administration/Software Sources menu. Add the online repositories for main restricted , updates and security.

---

### Post by Kakers on 2010-02-25
Not sure that would cause a problem as that just excludes that line. Thanks for all your help though as it has helped me narrow things down... I think I'm just going to have to reinstall the OS :(

---

### Post by MooPi on 2010-02-25
No it's in your apt list and can be corrected :(:(:( It looks as if you installed from CD without adding the online repositories.
This is what mine looks like. Notice the difference.

> # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

---

### Post by crash123 on 2010-02-27
I just started having this exact same problem this morning, completely out of the blue. But I then tried to open synaptic through the terminal, and it worked fine with no error messages or anything. Now it works fine if I open it from Administration, too. I have no idea. I literally did nothing to try to fix the issue and didn't change anything on my computer at all, but for some reason it just started working normally again. 

I've had the same thing happen with Google Chrome once, too, and the problem ended up solving (I guess?) itself in the same way. Weird.

---

