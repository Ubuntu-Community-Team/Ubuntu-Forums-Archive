---
title: "apt-get dependency problems"
date: 2005-08-12
forum: Desktop Environments
---

### Post by kinus on 2005-08-12
I somehow have seem to have broken my apt-get and am constantly getting dependency problems. I choose to use apt-get because it automatically resolves dependencies. However, whenever I try to install something i get several dependency failures.

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  klavaro: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
           Depends: libgtkextra17 but it is not going to be installed
  splashy: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
           Depends: libdirectfb-0.9-20 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

klavaro and splashy are two packages which i tried to install before and couldn't becuase they had the same dependency issues. Anyone have any ideas of how i can solve this issue?

---

### Post by Gezzer on 2005-08-12
in kynaptic go to the admin section & install synaptic

once installed & running
top bar settings then repositories
tick everything listed

then try your install ...

---

### Post by GeneralZod on 2005-08-12
I've had the same experiences with splashy.  I'm not entirely sure what's happened, but apparently more and more people are compiling against this new version of libc.  Here's a backports request post that refers to this as a "famous" problem:

[http://ubuntuforums.org/showthread.php?t=46861](http://ubuntuforums.org/showthread.php?t=46861)

I'd be very interested to hear more about the issue and why it is occurring.

In a nutshell, I don't think you've broken apt; it's just that recent debs have been using a more up-to-date version of a library that is so fundamental  that it probably can't be safely upgraded in Ubuntu.  At least, not until Breezy :)

---

### Post by kinus on 2005-08-12
Well I guess it was due to the famous libc6 problem. From what GeneralZod said I decided to check whether or or not splashy had been installed even though the installation process supposedly had..and low and behold it has. Did a quick dpkg --remove for splashy and then again for klavaro and once again my apt-get works. Thanks for all the suggestions :) 

BTW, does anyone have a nice sources.list which includes lots of repositories? And if so would they post it/email it.

Thanks.

---

### Post by Gezzer on 2005-08-12
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

#### backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 

##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main 
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main

---

### Post by gregb49 on 2005-08-14
Thanks Gezzer - this solved a problem for me that I had when I got an insert hoary CDROM message everytime I tried to install the kubuntu desktop. Your sources list solved the problem. Greg

---

### Post by daller on 2005-08-15
I'm new to Ubuntu, but isn't "multiverse" the same as "non-free" in Debian?

...In such case - Shame on you! :)

---

