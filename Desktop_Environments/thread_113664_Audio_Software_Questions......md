---
title: "Audio Software Questions....."
date: 2006-01-06
forum: Desktop Environments
---

### Post by crispy_420 on 2006-01-06
Any audio app I try to install wants libjack. I have that install but it wants a different version. The apps I want are rosegarden and muse. I finally found the version of libjack I need but jackd is the wrong version.

Anyone have any luck with these audio apps? And they even worth an install? I'd like to get that resolved because it seems this a problem I always seem to have.

Do I need to get some new repositories? Or enable more?

On a side note, any good apps to record Shoutcast Streams? Or do I just need to listen to them with a different app then I currently use (xmms)?

And is it possible to "record what you hear" in Audacity just like in windows?

Any help will appreciated. Thanks!

---

### Post by 23meg on 2006-01-06
How are you trying to install rosegarden and muse? They're in the repositories so why don't you install from there?

---

### Post by crispy_420 on 2006-01-08
That is what I'm trying to do and I keep getting dependency issues. First it wants a different version of libjack. Then I try to install the correct version of libjack, the one wanted by muse/rosegarden, and the I get an dependency problem with jackd.

Should I get more repositories that may have the versions of libjack and jackd or will these just cause other dependency issues causing other software not to work?

---

### Post by FarEast on 2006-01-08
I could install both muse and rosegarden4 with APT, though I have not learned
how to use them:) .  I wish I could use them in the future...

Here is my /etc/apt/sources.list .

```
deb http://jp.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu breezy main restricted

deb http://jp.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
```

Installed packages are the following:

jackd 0.99.0-2ubuntu1
libjack0.80.0-0 0.99.0-2ubuntu1
muse 0.7.1+0.7.2pre2-4
rosegarden4 1.0-1ubuntu3

---

### Post by crispy_420 on 2006-01-08
All is fine except jackd. I have a newer version but the older one that these apps need is not showing up.

**Here are my exact errors:**

libjack0.80.0-0:
  Depends: jackd (=0.99.0-2ubuntu1) but 0.100.0-4 is to be installed

muse:
 Depends: libfluidsynth1 but it is not going to be installed
 Depends: libjack0.80.0-0 but it is not going to be installed

rosegarden4:
 Depends: libjack0.80.0-0 but it is not going to be installed

And I also found another app that looks promising.

lmms [http://lmms.sourceforge.net/]("http://lmms.sourceforge.net/")

But is not in apt. Time to look for some new repositories. All my problems center around libjack & jackd. _Anyone know of a good source/repository?_

I did try your sources but no luck with my two trouble files. Getting late so I'll try in the morning.

---

### Post by FarEast on 2006-01-08
> libjack0.80.0-0:
> Depends: jackd (=0.99.0-2ubuntu1) but 0.100.0-4 is to be installed

It is odd that APT will install the version:confused: 
Pasting your souces.list may help in making out the cause.

---

### Post by crispy_420 on 2006-01-08
The older version doesn't show up in apt...

**_sources:_**

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free
 deb-src [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free 
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main


deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras multiverse
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
deb [http://apt.bxlug.be](http://apt.bxlug.be) ooo/ # packages additionels pour openoffice




deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

 deb [http://repos.knio.it/](http://repos.knio.it/) unstable main contrib non-free 
 deb-src [http://repos.knio.it/](http://repos.knio.it/) unstable main contrib non-free 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) experimental main
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

**I know it is a mess but haven't had the time to clean up. There are probally atleast a few duplicate entries.**
This is my first install of ubuntu and it has been one big experiment to test for organized install. It is so big because of search for multimedia app.

---

### Post by lamego on 2006-01-08
The probelm is that you have configured a lot of APT repositories which are not Ubuntu related and which will bring you dependency conflicts and eventually break some packages.
You should not add non-ubuntu repositores unless  you realy know what you are doing.
Clean your apt list, use the ubuntu with universe and multiverse enabled and then install. If it rosegarden does not install smoothly (as it did for me) then you have already broken some of your packages dependencies.

---

### Post by crispy_420 on 2006-01-08
Like I said early this was a test system that has been running for months. From first install of ubuntu. I just got a WD hard drive back from RMA and a soon as I get a new removable drive I will do a proper install.

But I just did what you said and it comes back to the libjack needing jackd, in different versions that don't even show up in apt.

But now it is time to do that fresh install on a 20GB drive to test. I can live without these apps but I was just going to test them for a friend in order to get him to switch to ubuntu (he's trying to run WinXP with 256MB DDR).

What is holding him up is wireless connection and media apps.

I'll do that install right now and only use proper sources and see that is my issue.

THANKS.

---

### Post by crispy_420 on 2006-01-08
You were right about broken packages. I did a quick install on a small drive as a test and the software(muse,rosegarden,etc.) installed just fine. And I just used ubuntu repos. Guess I'll do a reinstall on a larger drive. Atleast it will be quicker install than windows.

Is there an easy/quick way to transfer my settings over to a new install or do I have to start from scratch?

THANKS FOR THE HELP!!!

Or do I have to do a reinstall? Can I some how repair?

---

### Post by lamego on 2006-01-08
If you are talking about user related settings, like your desktop icons, application settings etc is just simple as backing up your /home .

It is possible to repair but you would need to know which packages have broken your system, remove them and install from ubuntu.
You could try to look on the other system you just installed and check for the package names and versions related to your problem...

---

### Post by crispy_420 on 2006-01-08
I'm in my new install and this time I'm going to do it right. I'll just backup all that I have(icons, music, etc.) and start off from scratch. LIke I said the first install was a test. When I'm done and sure I backed up all that matters, wipe the drive and use it to "test" a different OS. But I'll be back because this has been my favorite linux distro I have used to date.

Thanks for the help.

---

### Post by crispy_420 on 2006-01-09
So to save all my settings I can just transplant my /home folder. Will that cover my TV tuner card configuration too? It was a pain to setup for NTSC (modify a config file as the TVtime site suggested and hope it works).

I would like to avoid a long setup. Is there any tools that can simplify the whole process for me?

And would my theme/appearance crossover too?

Is it so wrong that I want the transition to be as smooth as possible? That way I can head back to playing.

And as far as the drive my messed up OS is on, I'll try playing with Dapper.

Thanks in advance.

Oh, I had to edit something too.
Just a newb question: Are all repos the same?
If I add security, backports, etc. are they all the same and I don't need more than one security as they cover the same packages? Just want to make sure I don't duplicate the same mistakes again and so I can have a much shorter sources list.

---

