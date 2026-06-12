---
title: "Ubuntu Based or Debian Based"
date: 2022-06-10
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-06-10
I am puzzled a wee bit when certain distros are referred to as Ubuntu or Debian based.

Ubuntu I know is Debian based but another popular distro, Mint is apparently Ubuntu based, why is this not referred to as Debian based?

Linux MX is referred to as Debian based, the popular RaspberryPi_OS is also Debian based 

Appreciate both Ubuntu and Debian have different desktops available but I'd appreciate anyone's opinion on this, maybe it is just the repositories used.

Geoff

---

### Post by TheFu on 2022-06-10
Ubuntu mixes which debian software it grabs for the base of each Ubuntu release.  There is a mix of stable and testing packages are used. [https://ubuntu.com/community/debian](https://ubuntu.com/community/debian)  Also, Canonical adds some Canonical-only software to their releases and setup some different defaults based on their goals.

Mint has both Ubuntu-based [https://www.linuxmint.com/download.php](https://www.linuxmint.com/download.php) and Debian-based [https://www.linuxmint.com/download_lmde.php](https://www.linuxmint.com/download_lmde.php) versions.  These would have slightly different versions of software included, since debian stable won't have non-stable, i.e. "testing" versions.

Part of the reason I've chosen Ubuntu rather than Debian is for this slightly newer versions of some software.  Sometimes that turns out less-great.

---

### Post by #&amp;thj^% on 2022-06-10
Is Mint based on Ubuntu or Debian?
Linux Mint is a (partly) community-maintained distribution, supported by donations and advertisements. Their flagship product is based on Ubuntu, but they also provide a “Linux Mint Debian Edition” variant that evolves continuously (as it is based on Debian Testing).

Is Mint the same as Debian?
If you're connecting the dots, that means that Linux Mint is ultimately based on Debian. But Linux Mint is not Ubuntu, and Ubuntu is not Debian. While they may largely share the same technical underpinning, chances are you won't have that impression when you boot them up for the first time.

Over time, Mint differentiated itself from Ubuntu further, customizing the desktop and including a custom main menu and their own configuration tools. Mint is still based on Ubuntu – with the exception of Mint's Debian Edition, which is based on Debian (Ubuntu itself is actually based on Debian).
Clear as Mud Right?

---

### Post by mIk3_08 on 2022-06-11
For me, why Mint is a Ubuntu based Operating System because the core of Mint Operating System came from Ubuntu resources and it is also called as Debian due to Ubuntu is also a Debian based. While Google is a Highly Modified Hybrid Debian Machine it is what it is. the core of it, is Linux. :o Regards and cheers.

---

### Post by guiverc on 2022-06-11
I'm a user of both Debian & Ubuntu.  Currently I'm using Ubuntu with the LXQt desktop (ie. Lubuntu)..   The version of my desktop is LXQt 1.1, ie.

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   lxqt-about --version
lxqt-about 1.1.0
liblxqt   1.1.0
Qt        5.15.4
guiverc@d960-ubu2:/de2900/lubuntu_64$   rmadison lxqt-about
 lxqt-about | 0.10.0-3        | xenial/universe  | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 lxqt-about | 0.12.0-4        | bionic/universe  | source, amd64, arm64, armhf, i386, ppc64el, s390x
 lxqt-about | 0.14.1-1ubuntu2 | focal/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 lxqt-about | 0.17.0-0ubuntu1 | impish/universe  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 lxqt-about | 0.17.0-0ubuntu1 | jammy/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 lxqt-about | 1.1.0-0ubuntu1  | kinetic/universe | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

Later today I'll be using a Debian system (*bookworm, or Debian testing*) and the LXQt version will be the older version I had early in 2019 (ie. the version that was in Lubuntu 19.04) 

Version you'll see in Debian can be seen with

```

guiverc@d960-ubu2:/de2900/lubuntu_64$   ssh de2900 -C 'rmadison lxqt-about'
lxqt-about | 0.11.1-1      | oldoldstable   | source, amd64, arm64, armel, armhf, i386, mips, mips64el, mipsel, ppc64el, s390x
lxqt-about | 0.14.1-1      | oldstable      | source, amd64, arm64, armel, armhf, i386, mips, mips64el, mipsel, ppc64el, s390x
lxqt-about | 0.16.0-1      | stable         | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
lxqt-about | 0.16.0-1      | testing        | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
lxqt-about | 0.16.0-1      | unstable       | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
lxqt-about | 0.16.0-1      | unstable-debug | source

```

My point is whilst most code in Ubuntu is from upstream Debian, that's not always the case.  This Ubuntu box had `grub 2.06` many months before my Debian *testing/sid* box got that version, which initially created some issues for me. (*my systems are dual boot & other OSes weren't detected*). Sure that issue got fixed soon enough as most do (*fun of being on a development release is you discover issues early*), but don't assume Debian is always ahead of Ubuntu given it's * upstream* (*real life is more complicated with what goes into a distribution  coming from many streams!*).

(Contrast point:  I've discovered an issue on my Debian *testing/sid* box that hasn't hit my Ubuntu box yet... in that case the package(s) involved are newer in Debian, and I'm waiting for them to hit Ubuntu too, so I can file a bug with Ubuntu; which I'm hoping will get more attention than the upstream (Debian) bug received).

Me I'm involved with Lubuntu, the Lubuntu team contains beyond Lubuntu *developer*, we have 2x *Ubuntu* Core-Devs with both Core-Devs being involved with Debian too (a DD (Debian Developer) & DM (Debian Maintainer)). It's the same elsewhere in Ubuntu too, eg. you'll see Ubuntu-MATE, Xubuntu .. *devs* pushing code to Debian on occasion so it'll feed back to Ubuntu where they want it; but if Debian is in freeze etc. the upstream-Debian is just skipped.  I suppose I'm saying there is *overlap* and a lot of working together between Debian & Ubuntu (*if you go look on IRC you'll find a #debian-ubuntu room specifically for that purpose*)

A GNU/Linux distribution is filled with many components, taking from many other projects, and the mention of another distribution is a *clue* as to where many packages come from.  Key is to assume that's the only place they come from.

(*Apologizes for length, and lack of clear response*)

---

### Post by ajgreeny on 2022-06-11
I have been using debian-unstable with Xfce (as a virtual machine) for a few months now simply to see how different it is from Xubuntu and so far have had no problems with it.

Using any of the debian based OSs gives a great deal of familiarity in use and I think I could very easily manage Debian-unstable as my main daily use machine should it become necessary for any reason.

One reason for not using it all the time used to be the lack of the use of firefox other than the esp version but having now started using the downloaded tar.gz archive as my Firefox version I know it can also be run in that way in any debian version, thus removing that difficulty.

Both Debian and Ubuntu are great systems with very many similarities. Why not give some versions of debian a try yourself  as VM if you prefer.

---

### Post by grahammechanical on 2022-06-11
My view of this question is that it all depends upon the source or  origin of the main packages in the distribution. For Ubuntu it is  Debian. For Linux Mint it could be Ubuntu or Debian depending on the  edition.  

Another factor to consider is the location of the  software repositories. Canonical maintains the software repositories of  Ubuntu. Do the Linux Mint developers maintain their own Linux Mint  repositories? Or, do they make use of Ubuntu repositories for the  edition based upon Ubuntu and make use of Debian repositories for the  Debian edition?

I do not think it accurate to describe Linux Mint based on Ubuntu as Debian based.

Regards

---

### Post by #&amp;thj^% on 2022-06-11
This should help:
```
deb http://packages.linuxmint.com una main upstream import backport

deb http://archive.ubuntu.com/ubuntu focal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ focal partner

#deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
Where they source their software.
Debian repos:
```
deb http://packages.linuxmint.com/ debian main upstream import
deb http://debian.linuxmint.com/latest testing main contrib non-free
deb http://debian.linuxmint.com/latest/security testing/updates main contrib non-free
deb http://debian.linuxmint.com/latest/multimedia testing main non-free

deb http://ftp.us.debian.org/debian/ testing main contrib non-free
deb http://ftp.us.debian.org/debian/ unstable main contrib non-free
deb http://ftp.us.debian.org/debian/ experimental main contrib non-free
```

---

### Post by Geoff_Lane on 2022-06-13
> **mIk3_08 said:**
> For me, why Mint is a Ubuntu based Operating System because the core of Mint Operating System came from Ubuntu resources and it is also called as Debian due to Ubuntu is also a Debian based. While Google is a Highly Modified Hybrid Debian Machine it is what it is. the core of it, is Linux. :o Regards and cheers.

Yes, appreciate Google's Android and Amazon's Fire are effectively proprietary closed source variants of Linux.

Geoff

---

### Post by Geoff_Lane on 2022-06-13
My main system is Ubuntu though I have 5 Raspberry Pi devices running.

I also have Linux MX on my main hard drive but on an external drive have Debian and Arch.

So my auto boot is in to Ubuntu and the one I am familiar with, I do like Debian on my external drive, nice that all my Ubuntu files are available to it too.

As for Arch, it was an experimental installation, neat, got X11 and Desktop working with it and can understand why many like it, very vanilla and able to add what one wants.

Geoff

---

### Post by mIk3_08 on 2022-06-14
> **Geoff_Lane said:**
> Yes, appreciate Google's Android and Amazon's Fire are effectively proprietary closed source variants of Linux.
Geoff That is why we should keep the fire burning. Its the Linux machine brings the world to the next generation of internet. Regards and Cheers.

---

