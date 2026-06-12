---
title: "Failed install of KDE on ubuntu"
date: 2006-11-19
forum: Desktop Environments
---

### Post by LinuxRush on 2006-11-19
Hi guys,

I tried to install KDE-DESKTOP on ubuntu 6.10.

everything went fine except at the end I saw this:

> Errors were encountered while processing:
 ksysguardd
 ksysguard
 kubuntu-desktop


And in synaptic, ksysguardd is listed under "broken" packages.

here's my sources file:
> 
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free       
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


however, with this source list, i cannot re-install ksysguardd... it errors out with this message:

> E: /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb: trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour


what am I doing wrong?

-LR

---

### Post by arnieboy on 2006-11-19
do the following:
```
sudo apt-get remove bonjour
```
and then try again

---

### Post by popeyeray on 2006-12-03
[B][COLOR="Blue"]Ok I had all the errors you had and found the answer here:
[http://ubuntuforums.org/showthread.php?t=283683]("http://ubuntuforums.org/showthread.php?t=283683")
What I did was removed the offending file, remember to go to your /var/cache/apt/archives/ and manually delete the "libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb". If your using synaptic search for "libdnssd1" and choose to completely uninstall, you may find it is still on your computer is the archives directory that's why I mention you should manually delete it. 
What I did is completely unistall the following files:
bonjour
libavahi-compat-libdnssd-dev
libnss-mdns
service-discovery-applet
You may or may not have these files installed, but if they are completely uninstall them.
 which come up when you search for bonjour, they are related and will also uninstall KDE and many other files, DON'T WORRY, you can reinstall them afterwards.
I restarted but i'm just paranoid that way, I got a message about beagle something or another not starting but I figured that was because I uninstalled KDE. 
I then re-installed KDE and also searched for beagle and checked everything there, eight items all together, some were already installed but I didn't want to take a chance. 
The point here is that you have to uninstall libavahi-compat-libdnssd1, then uninstall bonjour, then reinstall libavahi-compat-libdnssd1, then reinstall bonjour because the a file in bonjour is in conflict with libavahi-compat-libdnssd1 but if you install libavahi-compat-libdnssd1 first then you should be able to install bonjour, I DID NOT because I don't really need it.
So now everything works in KDE/Kubuntu desktop and Gnome. Hope this helps.[/COLOR][/B]:)

---

### Post by arunsub on 2006-12-12
I have to same problem. When i try to remove bonjour with sudo apt-get remove bonjour, I get the following error:
The following packages have unmet dependencies:
  ksysguardd: Depends: libavahi-compat-libdnssd1 (>= 0.6.13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When i tried sudo apt-get -f install, I get this error:
After unpacking 102kB of additional disk space will be used.
(Reading database ... 149991 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I deleted libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb and renamed libdns_sd.so.1, but still it's not working. My apt-get/synaptic is broken now. Please help.

---

### Post by arunsub on 2006-12-12
I cancelled the update to libavahi through Adept and I could install the rest of the pacakages fine.

---

