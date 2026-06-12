---
title: "Audacity - missing dependency"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-04-13
I'm trying to install Audacity, via Synaptic.  I'm being told that there's a missing dependency:

**[INDENT]libwxgtk2.4-1[/INDENT]**

and it suggests that I should make sure the right repos are enabled.  But...as far as I can see, I have all the usual suspects in my sources.list.

Any ideas?  Any other repos I need to  add?  The contents of my sources.list is: 

```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

[COLOR="Silver"]## Major bug fix updates produced after the final release of the
## distribution.[/COLOR]
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

[COLOR="Silver"]## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.[/COLOR]
deb-src http://archive.ubuntu.com/ubuntu breezy universe

[COLOR="Silver"]## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.[/COLOR]
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://people.ubuntu.com/~doko/OOo2 ./


```

---

### Post by Ramses de Norre on 2006-04-13
sudo gedit /etc/apt/sources.list
add line ```
deb http://archive.ubuntu.com/ubuntu breezy universe

```
Now you've got only the universe source repo and you need the binary one.
After that do sudo apt-get update && sudo apt-get install libwxgtk2.4-1
If that's not the right package try sudo apt-get install libwxgtk2.4-1-contrib

EDIT: you'll want to add ```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
``` too , I don't know why you haven't got those binary repo's, they are used mostly.

---

### Post by Edward The Bonobo on 2006-04-13
Merci.  But what   I alreadly have is:

```

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

```

This should work, n'est-ce pas?

I don't know where I got that sources.list from.  It looks a bit screwed up.  I think Automatix may have over-written my old one.  Can you post a suitable sources.list to cover all the Ubuntu repos?




btw - I have a solution to turning a .rm stream into .mp3, using vsound, sox and lame.  I'll write a HowTo.  Now I want to use Audacity to chop up my large .mp3.

---

### Post by Ramses de Norre on 2006-04-13
Ok, it was indeed allready there, but it's difficult to find whith that strange lay out;)
This is my sources.list:
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

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

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## penguin liberation front primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## penguin liberation front secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## penguin liberation front mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
deb http://people.ubuntu.com/~doko/OOo2 ./

```
Where you able to install the needed package?
If not what's the error?

---

### Post by Edward The Bonobo on 2006-04-13
Merci encore.  Surtout pour les repositories de la PLF.

No, it wouldn't install Audacity.   The error was 'Missing dependency: libwxgtk2.4-1'

Yes - a very strange layout...but not mine.  I blame Automatix.

---

### Post by Edward The Bonobo on 2006-04-13
Ah! No.  It's not the repos.  It's another problem...maybe bad dependencies in Audacity:

```

myusername@cpc1-eswd2-4-1-cust78:~$ [COLOR="DarkRed"]sudo apt-get install libwxgtk2.4-1[/COLOR]
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
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
E: Broken packages
myusername@cpc1-eswd2-4-1-cust78:~$ [COLOR="Sienna"]sudo apt-get install audacity[/COLOR]
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
  audacity: Depends: libwxgtk2.4-1 (>= 2.4.4ubuntu5) but it is not going to be installed
E: Broken packages
myusername@cpc1-eswd2-4-1-cust78:~$

```

Any more ideas?

---

