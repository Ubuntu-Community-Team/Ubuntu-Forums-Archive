---
title: "I screwed up my source list ;_;"
date: 2008-12-19
forum: General Help
---

### Post by Zaosyn on 2008-12-19
Heya. I haven't been using Ubuntu long at all, infact the commands still confuse me and I find myself using Google for simple how-tos for using Ubuntu. 

I was reading a guide on installing Java on Ubuntu ([http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)) and I added the links the page gave into my Source list and from there it's been chaotic. Right now when I try to open up my Package Manager I get this error:

```
 E: Type '[sudo]' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```
I don't know where to access the repository dialog. I Google'd it and got nothing helpful ;_;. 
Here's what my Source List looks like
```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
* deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse

## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.edit /etc/apt/sources.list
[sudo] password for tyler: 

# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

If you know of any way to reset my Source list I'd really appreciate it, any posts are very much appreciated :]. I'm a very simple person, all I need is to install Java and I've seem to dug myself into a hole here :P

---

### Post by blazemore on 2008-12-19
Here you go dude

```
sudo gedit /etc/apt/sources.list
```

Replace it all with this:

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse

## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    * deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by hyper_ch on 2008-12-19
I also created a little generator for the sources list. Have a look at my sig.

---

### Post by blazemore on 2008-12-19
The sources list has very precise syntax.
If you'd looked at the error, you would have seen there was a random entry on line 50 that clearly wasn't defined.

Also, there were a lot of *s dotted around everywhere; when you copy entries off the Internet, you shouldn't directly edit the sources.list file unless you know what you're doing (no offense mate but I don't think you do)

Instead, use the Software Sources tool:
```
System->Administration->Software Sources
```

---

