---
title: "libsdl1.2-dev won't install"
date: 2006-02-14
forum: Desktop Environments
---

### Post by eRoot on 2006-02-14
I'm trying to install SDL for my development needs, so I searched and found libsdl1.2-dev. Very well. I tried to install the package, but it gave me the following error: 

```
barry@box:~/Progs$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
```

So there's something up with libartsc0-dev. I figured I could try and install it seperately. No success:

```
barry@box:~/Progs$ sudo apt-get install libartsc0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.4.3-0ubuntu1) but 1.5.1-0ubuntu0breezy1 is to be installed
E: Broken packages
```

I don't completely understand that message. Nevertheless, I tried to install libartsc0

```
barry@box:~/Progs$ sudo apt-get install libartsc0
Reading package lists... Done
Building dependency tree... Done
libartsc0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
barry@box:~/Progs$
```

I give up. I couldn't find anything usefull on the forum search, so I have to ask you.
Below is my sources.list, just in case that might be important.

Repos:
```
## new repository list

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

## audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious
```

Thanks in advance.

---

### Post by Ramses de Norre on 2006-02-14
You could try installing the .deb from [http://packages.debian.org/unstable/libdevel/libsdl1.2-dev]("http://packages.debian.org/unstable/libdevel/libsdl1.2-dev") both packages are listed there.

---

### Post by eRoot on 2006-02-14
That worked like a charm! If anyone has the same problem: I installed "libartsc0" first, then "libartsc0-dev" and finally "libsdl-dev". 

Thank you very much.

---

### Post by XDevHald on 2006-02-14
How were you able to grab the deb from the mirror if the mirror is down from the Debian packages site?

> packages.debian.org is down at the moment due to performance issues.   We apologize for any inconvenience and hope to have service restored as soon as possible.


---

### Post by eRoot on 2006-02-15
The mirror refers to a back-up server. I simply changed the url so it stated the same spot on the back-up server.
[http://pdo.debian.net/unstable/libdevel/libsdl1.2-dev](http://pdo.debian.net/unstable/libdevel/libsdl1.2-dev)

---

