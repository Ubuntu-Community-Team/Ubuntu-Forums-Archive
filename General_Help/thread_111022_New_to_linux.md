---
title: "New to linux"
date: 2006-01-01
forum: General Help
---

### Post by chadsmith on 2006-01-01
New to linux, but old to computers.

Took an old system and blew away NT4.0 and installed Ubuntu.  Now I need to learn how to use it.

First I've been trying to install java, but have had no luck.  I've made it all the way through the steps, but yet it doesn't work when I go to [www.popcap.com](www.popcap.com) 

Second, I prefer Opera over Firefox but have not had much sucess getting it installed.  I've tried with the deb version and the tar.gz version with no luck.  The tar.gz seemed to install without problems, but than I couldn't find it or get it to run when I found its directory.

Any help would be appreciated.

Chad

---

### Post by atoponce on 2006-01-01
I can't help you with the Java, as I have not had much luck in that area myself.  And the Ubuntu doc is out of date as it no longer works.  However, for Opera, it's easy.  Just visit the Opera page, download it for Ubuntu using the deb native format (do not check the box asking to download int TAR.GZ format).  Once downloaded, you need a library before you can install.  Pull up a terminal and type the following:

```
sudo apt-get isntall libqt3-mt
```

Once that library is installed, in your terminal:

```
sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
```

(or whatever the name of the file is).  That's it!  You should have a running Opera installation now.

---

### Post by JamesNorris on 2006-01-01
[QUOTE=chadsmith]New to linux, but old to computers.

Took an old system and blew away NT4.0 and installed Ubuntu.  Now I need to learn how to use it.

First I've been trying to install java, but have had no luck.  I've made it all the way through the steps, but yet it doesn't work when I go to [www.popcap.com](www.popcap.com) 

Second, I prefer Opera over Firefox but have not had much sucess getting it installed.  I've tried with the deb version and the tar.gz version with no luck.  The tar.gz seemed to install without problems, but than I couldn't find it or get it to run when I found its directory.

Any help would be appreciated.

Chad[/QUOTE]


What exaclty is going wrong? There is a java-plugin in the repositories for browsers. I don't know about opera, but in firefox, I just used apt-get to install it. 

Have you added the extra repositories for apt?

There shouldn't be a problem installing opera's .deb if you selected the ubuntu version... Maybe it has dependencies that you still need to apt-get. 

If you have any error messages, they will help. Post them here.

---

### Post by rjwood on 2006-01-01
search for automatix by arnieboy. They are both there. Good Luck and Welcome to the forums.

---

### Post by chadsmith on 2006-01-01
Okay, I tried Opera one more time.  Here is what it says when I try to install the library.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt-mt


And here is what I get when I try to install Opera

Selecting previously deselected package opera.
(Reading database ... 56814 files and directories currently installed.)
Unpacking opera (from opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


Chad

ps  what are the shortcut keys for cut & paste (ie windows is CTR C & CTR V)?

---

### Post by Madpilot on 2006-01-01
Ctrl+C & +V are still the cut & paste keys in Ubuntu.

As for Opera, I'm running it right now to type this, so it really does run in Ubuntu! Have a look here - [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser) - for Opera in Ubuntu.

Oh, and watch out for Automatix, it seems to break a rather large number of Ubuntu installs...

---

### Post by Bachstelze on 2006-01-01
@chadsmith > you need to enable universe/multiverse repositories. Run

```
sudo gedit /etc/apt/sources.list
```

then delete everything and paste this instead :

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

then save the file and run

```
sudo apt-get update
```

you should be OK to install whatever package then :)

---

### Post by TimelessRogue on 2006-01-01
Hey, welcome!  

As rjwood says, get Automatix installed ASAP and go from there ... it'll make your life so much easier.  Along that line, you'll be able to install all the Firefox add-ons (including Java), Java itself, Opera, etc.

Another word to the wise:  Don't overwhelm yourself by trying to make too many modifications 'til you've been into Ubuntu for a bit ... you'll only make things more complicated than they need to be, as well as more frustrating.

Again, welcome ... and come on back with any problems:  you'll get the answers here ...

---

### Post by chadsmith on 2006-01-01
Okay I'll look into that.  In the meantime I've been trying a few things to get Opera installed and no luck.  Here is a C&P from the terminal on the last attempt.

root@chad:/home/chad# sudo apt-get update
Reading package lists... Done
root@chad:/home/chad# sudo apt-get install opera
Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
root@chad:/home/chad#


Chad

---

### Post by Bachstelze on 2006-01-01
I don't think Opera is available through the repos. Use automatix or go to Opera website downloaed the UBUNTU (NOT Debian) .deb package. Install it by typing

```
sudo dpkg -i pakage_name.deb
```

---

### Post by atoponce on 2006-01-02
[quote=chadsmith]Okay, I tried Opera one more time.  Here is what it says when I try to install the library.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt-mt


And here is what I get when I try to install Opera

Selecting previously deselected package opera.
(Reading database ... 56814 files and directories currently installed.)
Unpacking opera (from opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


Chad

ps  what are the shortcut keys for cut & paste (ie windows is CTR C & CTR V)?[/quote]

You need to install "libqt3-mt" not "libqt-mt".  When that is installed, Opera will install just fine.

---

