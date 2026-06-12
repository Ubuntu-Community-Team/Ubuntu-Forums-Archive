---
title: "NVU Help, i have looked at the official! (Solved)"
date: 2005-10-29
forum: Desktop Environments
---

### Post by mit on 2005-10-29
Hi,

I have looked at the official but cannot install NVU. :( 

It says it is not Universe and needs to be installed manually. I downloaded the Debian based [http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2]("http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2") but it will not install. 

I have tried the instructions but have had no luck with either that one and dont know what Ubuntu PPC is and cannot find it on the site anyhow.

The instructions i have followed are [https://wiki.ubuntu.com/InstallingNvu?highlight=%28NVU%29]("https://wiki.ubuntu.com/InstallingNvu?highlight=%28NVU%29")

Thanks for looking :KS

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=mit]Hi,

I have looked at the official but cannot install NVU. :( 

It says it is not Universe and needs to be installed manually. I downloaded the Debian based [http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2]("http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2") but it will not install. 

I have tried the instructions but have had no luck with either that one and dont know what Ubuntu PPC is and cannot find it on the site anyhow.

The instructions i have followed are [https://wiki.ubuntu.com/InstallingNvu?highlight=%28NVU%29]("https://wiki.ubuntu.com/InstallingNvu?highlight=%28NVU%29")

Thanks for looking :KS[/QUOTE]


weird, it's in my repos...

here is a copy of my sources.list (ubuntu 5.10 386/686):
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by matthew on 2005-10-29
It's in breezy-universe. Here's proof:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=breezy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=breezy&release=all")

---

### Post by aysiu on 2005-10-29
Visual proof, too.

---

### Post by mit on 2005-10-30
Oh, i wonder why it isn't in mine? I have tried searching for nvu and NVU (not that lower/uppercase would make a difference would it?

All the repositries are enabled. :confused:

---

### Post by towsonu2003 on 2005-10-30
[QUOTE=mit]Oh, i wonder why it isn't in mine? I have tried searching for nvu and NVU (not that lower/uppercase would make a difference would it?

All the repositries are enabled. :confused:[/QUOTE]

try copy pasting your sources.list file here. maybe someone can help you using it. here is the path:

/etc/apt/sources.list

---

### Post by aysiu on 2005-10-30
[QUOTE=mit]
All the repositries are enabled. :confused:[/QUOTE] What does that mean--*all* the repositories are enabled? Are you sure? Well, the ones I used are following these directions:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by stoeptegel on 2005-10-30
/offtopic

[QUOTE=aysiu]Visual proof, too.[/QUOTE]

XFCE right? Damn they have a nice GUI too.

---

### Post by aysiu on 2005-10-30
[QUOTE=stoeptegel]/offtopic



XFCE right? Damn they have a nice GUI too.[/QUOTE] /still offtopic

Yes, it's XFCE. It's actually using a theme I installed in Gnome, believe it or not.

---

### Post by mit on 2005-10-30
here goes!

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Sorry, i realise this should be in the 5.04 section. Please look [http://ubuntuforums.org/showthread.php?p=455686#post455686](http://ubuntuforums.org/showthread.php?p=455686#post455686) at this thread for the Synaptic error which i believe is linked as to why i can't get NVU installed.

Thanks for looking

---

### Post by mit on 2005-10-30
When i open Synaptic i get the following error. I also want to install NVU but it isn't there. 

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by aysiu on 2005-10-30
Mirrormax is no longer around.
Follow these directions:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

... meaning look at post #7 in this thread.

---

### Post by mit on 2005-10-30
thank you so much! NVU downloaded and installed a dream. My error has also gone in synaptic too. 

Thanks for your help. This forum is great and so is Ubuntu! :KS

---

