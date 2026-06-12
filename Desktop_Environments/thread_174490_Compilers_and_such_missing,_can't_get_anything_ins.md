---
title: "Compilers and such missing, can't get anything installed."
date: 2006-05-11
forum: Desktop Environments
---

### Post by OpticalIllusion on 2006-05-11
It seems like any time I try to install anything anymore, I have dependencys missing.  For instance, I'm trying to install 3D Desktop and it says I'm missing libncurses5 (= 5.5-1).  I've tried apt-get update and I've still got nothin.  Where can I get all the compilers and stuff needed to install most files?  :confused:

---

### Post by Sef on 2006-05-11
To compile, build-essential must be downloaded.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by Omnios on 2006-05-11
Here is a basic compiling guide.
[http://ubuntuforums.org/showthread.php?t=171822]("http://ubuntuforums.org/showthread.php?t=171822")

---

### Post by OpticalIllusion on 2006-05-11
When I try sudo apt-get install build-essential it's telling me that I'm missing the libncurses thing again.  :confused:

---

### Post by Nequeo on 2006-05-11
[QUOTE=OpticalIllusion]When I try sudo apt-get install build-essential it's telling me that I'm missing the libncurses thing again.  :confused:[/QUOTE]

What happens when you type 'sudo apt-get install libncurses5'?

---

### Post by OpticalIllusion on 2006-05-11
It says I already have the newest version.

---

### Post by Omnios on 2006-05-11
The libncurses5 in the rwpository is version 5.4.9 your compiler is looking for version " (= 5.5-1)."

---

### Post by OpticalIllusion on 2006-05-11
[QUOTE=Omnios]The libncurses5 in the rwpository is version 5.4.9 your compiler is looking for version " (= 5.5-1)."[/QUOTE]
Sounds like you're right.  Here's a screenshot of the error.

[IMG]http://i8.photobucket.com/albums/a48/speed_demon1965/Screenshotcopy.jpg[/IMG]

How do I get version 5.5-1?

---

### Post by OpticalIllusion on 2006-05-12
No one knows where I can get libncurses 5.5-1?

---

### Post by Nequeo on 2006-05-12
Ncurses 5.51 is in Dapper... (not officially released yet) No packages in Breezy should ask for it. Are you trying to install Dapper packages in Breezy? Can you please post the contents of the file /etc/apt/sources.list for us to take a squiz at? Thanks!

[EDIT] You can get nCurses 5.51 here: [http://packages.ubuntu.com/dapper/base/libncurses5](http://packages.ubuntu.com/dapper/base/libncurses5)

But I would reccomend that you DON'T. Not yet, anyway. I think you have, or are trying to install, packages from repositories that are for the wrong version of Ubuntu, or  otherwise broken. I'd rather we try and find out why your system is demanding the newer version, and fix that.

Otherwise you'll very likely end up with a system that's Half 5.10, half 6.06, and all broken. Ya know what they say, prevention is better than cure! 

[/EDIT]

---

### Post by OpticalIllusion on 2006-05-12
Sorry, I've only been using Linux for about 3 or 4 months now and am still learning.  I really don't have any idea why I'm getting these errors.

Here are the commands I've tried to use so far:

First, I enter in sudo apt-get update.

For build-essential:
sudo apt-get install build-essential

3D Desktop:
sudo apt-get install 3ddesktop

I get the same libncurses5 error for both of them.  Do I need to fix or repair my Ubuntu somehow?  I'm not really sure what is going on here.

---

### Post by Nequeo on 2006-05-12
[QUOTE=OpticalIllusion]Sorry, I've only been using Linux for about 3 or 4 months now and am still learning.  I really don't have any idea why I'm getting these errors.

Here are the commands I've tried to use so far:

First, I enter in sudo apt-get update.

For build-essential:
sudo apt-get install build-essential

3D Desktop:
sudo apt-get install 3ddesktop

I get the same libncurses5 error for both of them.  Do I need to fix or repair my Ubuntu somehow?  I'm not really sure what is going on here.[/QUOTE]

Can you please type 'gedit /etc/apt/sources.list' from the command line, and then copy the contents of that file into a post for us to look at? (Probably a good idea to put it inside a QUOTE tags, too.

I have my suspicions about what might have happened, but I'd like to see that file before I say anything - as it would probably only confuse you if I end up being wrong.

---

### Post by OpticalIllusion on 2006-05-13
Here it is.

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

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
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arnielistenremoved


---

### Post by OpticalIllusion on 2006-05-13
Well I took that hard way out and reinstalled Ubuntu.  I had nothing to lose anyway.  All is well. :D

Except, I got 3D Desktop installed and installed my ATI Driver for my video card and 3D Desktop doesn't work for some reason.

---

