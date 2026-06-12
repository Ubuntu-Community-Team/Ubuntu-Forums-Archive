---
title: "No new packages after adding repositories"
date: 2008-12-26
forum: General Help
---

### Post by brdlvelixir on 2008-12-26
Alright I'm stumped, I've installed and reinstalled ubuntu at least 5 times in the past week (for various reasons). Each time though, synaptic acts different. The first thing I ever do (after connecting to the internet) is run these commands:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free" | sudo tee -a /etc/apt/sources.list

and

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

then I open Synaptic and under settings -> repositories I check all except source code in the Ubuntu Software tab, and check all the boxes in Third Party Software tab, then update again with the Refresh button in synaptic. Why is it that after doing all this, SOMETIMES vlc, nvidia-glx-177, flash-plugin-nonfree, java6-jre, and many other apps are there, and other times, they aren't??? I haven't messed with the fresh install in any way except what I described above, but I get different results. Here is my sources.list contents:


user@user-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


-------------------------------------------------------------------

(I also added the google repository) Anyone know why the above mentioned packages are not showing up in synaptic after some ubuntu installs but are after others?

---

### Post by dcstar on 2008-12-26
> **brdlvelixir said:**
> Alright I'm stumped, I've installed and reinstalled ubuntu at least 5 times in the past week (for various reasons). Each time though, synaptic acts different. The first thing I ever do (after connecting to the internet) is run these commands:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free" | sudo tee -a /etc/apt/sources.list

and

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

then I open Synaptic and under settings -> repositories I check all except source code in the Ubuntu Software tab, and check all the boxes in Third Party Software tab, then update again with the Refresh button in synaptic. Why is it that after doing all this, SOMETIMES vlc, nvidia-glx-177, flash-plugin-nonfree, java6-jre, and many other apps are there, and other times, they aren't??? I haven't messed with the fresh install in any way except what I described above, but I get different results. .........
(I also added the google repository) Anyone know why the above mentioned packages are not showing up in synaptic after some ubuntu installs but are after others?

Because there is no guarantee that 3rd-party repositories are always available. If they cannot be contacted then Synaptic will not show their contents.

---

### Post by brdlvelixir on 2008-12-26
But, as an example, my mediubuntu repo is working its just not showing up in synaptic. I can isntall packages such as w64codecs, googleearth, and vlc with "sudo apt-get install" but when I search for the same package in synaptic nothing comes up..

---

### Post by bodhi.zazen on 2008-12-26
Did you refresh your package list ?

In synaptiic, reload. In the command line

sudo apt-get update

---

### Post by brdlvelixir on 2008-12-26
yes I did both.

---

### Post by brdlvelixir on 2008-12-26
alright, I guess they are there, but they just weren't showing up in the Quick Search bar, I had to click the search button next to it and type in the package and they were found.. still don't know why sometimes they showed up in quick search and sometimes not. oh well, thanks, solved

---

### Post by dcstar on 2008-12-27
> **brdlvelixir said:**
> alright, I guess they are there, but they just weren't showing up in the Quick Search bar, I had to click the search button next to it and type in the package and they were found.. still don't know why sometimes they showed up in quick search and sometimes not. oh well, thanks, solved

Quick search only filters what is already in the Synaptic main screen, it is **not** a general search tool.

Please give us ALL the details next time rather than holding back information that would have provided you with an answer in a few seconds.

---

### Post by brdlvelixir on 2008-12-28
alright dc dinkskin. I have synaptic open and on the left "All" is highlighted, so all the available programs are on the "synaptic main screen", yet still quick search returns no results for vlc. but when i scroll down i can see the package right there. quick search just isnt working. oh well apt-get works so no biggie sorry for wasting your valuable time.

---

### Post by RobMagus on 2008-12-29
I'm having the same problem!  I've done a fresh install of 8.10 on my laptop, and I have carefully followed directions to add medibuntu to my repositories.  I've updated and refreshed every time I've tried it, but the bug persists:

even with "All" highlighted in Synaptic, quick search still doesn't find any packages from medibuntu.  It's really annoying!  It makes me wonder what else isn't showing up in the "All" list.

I have Ubuntu 8.10 on my desktop and am not getting this problem on it, but I installed it a month ago.  Could this be a problem with the latest updates?

EDIT:  I just checked, and medibuntu packages aren't showing up when I look at the "Installed" status in Synaptic, and that's even -more- annoying.  If it's not indexing them properly, what's to say that synaptic doesn't see them when I try to update all packages too?  argh

---

### Post by asynchronous13 on 2009-01-08
Just had a similar problem trying to install ndiswrapper. Brand new computer, fresh install of Ubuntu 8.10-64bit. 

I could scroll down and find 'ndiswrapper' listed but the quick search box would not find it. (i thought there was something else going on for a long time, once I scrolled down, the package installed without a hitch).

---

### Post by asynchronous13 on 2009-01-08
Just had a similar problem trying to install ndiswrapper. Brand new computer, fresh install of Ubuntu 8.10-64bit. 

In Synaptic Package Manager I could scroll down and find 'ndiswrapper' listed but the quick search box would not find it. (i thought there was something else going on for a long time, once I scrolled down, the package installed without a hitch).

---

