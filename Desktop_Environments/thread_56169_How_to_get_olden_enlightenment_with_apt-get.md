---
title: "How to get olden enlightenment with apt-get?"
date: 2005-08-11
forum: Desktop Environments
---

### Post by kzu on 2005-08-11
I downloaded E with apt-get install enlightenment, but i think it's that new E17, atleast it looks like that and I don't see the bluesteel theme I downloaded anywhere... I especially want that older E. And sorry for flooding and spamming these boards full with my questions:D

---

### Post by varunus on 2005-08-11
If you install enlightenment from Hoary's built in repos, its Enlightenment DR16, not 17.  If you're using smoon's repos, it will be DR17.

Can you not get to the theme from "middle-click desktop->Themes"?  Mine shows up there.

---

### Post by kzu on 2005-08-11
About enlightenment shows 0.16.999.011. And if i middleclick it shows open programs and cleanup windows, nothing about themes. And the desktop looks like [this](http://www.mbnet.fi/~tupakki/e.jpg). And to be a little more specific, I can see the theme menu from that startbutton thing on the left bottom, but there's no bluesteel there :) I got it with apt-get too.

---

### Post by varunus on 2005-08-11
Yeah, that's E17.  Hehe.  Can you post your /etc/apt/sources.list file?

Another way to do it, open up synaptic, select the enlightenment package (and enlightenment-data), go to package->force version, and force it down to E16.

---

### Post by kzu on 2005-08-11
## The following lines pertain to supported packages:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## The following lines pertain to security updates:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

## Uncomment after release to continue getting updates:
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by 
## the Ubuntu team, and may not be under a free licence. This means that 
## software in these repositories WILL NOT receive any review or updates 
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and 
## 'multiverse' repositories:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

## Uncomment the following line to add Java software:
# deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

---

### Post by kzu on 2005-08-11
ok, now I removed the e17 one, got new and working sources.list and try to download and this is what I get:
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate


Did I mess something up when I tried that force version thing in synaptic ?

---

### Post by Diego F. on 2005-08-12
May be you can help me. I downloaded Enlightenment from Synaptic, but I see no way to load the new desktop. In the login, the session has no Enlightenment and the themes has the Gnome ones.

Am I missing something?

---

### Post by varunus on 2005-08-12
kzu,

I found the problem.  It seems you followed one of the enlightenment howtos on this site to get DR17; you set up an /etc/apt/preferences file, according to the howtos i've seen, where you pinned enlightenment to DR17.  You need to remove that file.

From the Enlightened GNOME post:
> 
I see you have the E17 repository (by swoon I think it is) in your sources.list file as do I. If you followed the howto on getting E17, then you need to delete the /etc/apt/preferences file that defines a higher priority for E17. I did this and I pulled down E16 with no problem.

Diego,

To get an entry for enlightenment, open a terminal and type:
```
sudo gedit /usr/share/xsessions/enlightenment.desktop
```
This will make a new blank file.  Add the following to it:
```
 [Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application
```

E should now appear in the login manager in the sessions menu.

---

### Post by Diego F. on 2005-08-13
Thank you!

---

### Post by kzu on 2005-08-13
It's working :) Aaah nice, I used this one 5 years ago when I last used Linux, and I think it's still the nicest one out there :)

---

### Post by Psquared on 2005-08-14
For some reason I am unable to get synaptic to download E16. I believe I have the right repos - I get no errors when I update in synaptic, but the error says:

> enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

My sources list is as follows:

> 
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ unstable main restricted
deb file:/var/cache/apt-build/repository/ apt-build main

## Uncomment the following two lines to fetch updated software from the network
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ unstable main main/debian-installer restricted restricted/debian-installer
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted

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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

#deb [http://public.planetmirror.com/pub/ubuntu-backports](http://public.planetmirror.com/pub/ubuntu-backports) hoary-backports main universe multiverse restricted
#deb [http://public.planetmirror.com/pub/ubuntu-backports](http://public.planetmirror.com/pub/ubuntu-backports) hoary-extras main universe multiverse restricted

#deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras main universe multiverse restricted

##Enlightenment
#deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

###Others
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

#deb [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/) testing main
#deb-src [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/) testing main
#deb [http://www.grawert.net/ubuntu/](http://www.grawert.net/ubuntu/) hoary universe

#deb [http://soulmachine.net/debian/](http://soulmachine.net/debian/) unstable/

#deb [http://digitalssg.net/debian/](http://digitalssg.net/debian/) stable main
#deb-src [http://digitalssg.net/debian/](http://digitalssg.net/debian/) stable main

#deb [http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/](http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/) ./
#deb [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./

#deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/
#deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/


Anyone got any ideas?

---

### Post by cjoshuav on 2005-08-14
For some reason I couldn't get E16 stable.  Isn't E17 still in beta?

Joshua

---

