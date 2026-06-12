---
title: "Where do I find a kernel-hedders?"
date: 2006-01-08
forum: General Help
---

### Post by Ixtok72450 on 2006-01-08
The reason I am looking for a kernel-hedder is because
I am trying to install Paralells-Workstation, so far without success. When trying to configure it I get: 


     Unable to find linux kernel source.
     To configure Parallels Workstation 2.0 you should have
     kernel source package for your Linux system installed.

using command uname -r tells me I have kernel 2.6.12-8-386

uning apt-get or synaptic looking for  kernel-hedders-2.6.12-8-386  gets me an error

E: Couldn't find package kernel-hedders-2.6.12-8-836

I have also tried

root@ubuntu2:/home/mark # apt-get install linux-hedders-2.6.12-8-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-hedders-2.6.12-8-386

also to no avail. 

Where can I find the proper kernel-hedders?  My repository file is:



deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

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
## repository.:

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

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
## created by arnieplanetremoved

I have found plenty for newer kernels but not for mine. Any Idea of what to do?


Thanks

Mark

---

### Post by duminas on 2006-01-08
You seem to be typoing your install command. That is, this is incorrect:
```
apt-get install linux-hedders-2.6.12-8-386
```
First and foremost, try this on the terminal (Applications > Accessories > Terminal).
```
$ sudo aptitude install linux-headers-`uname -r`
```This will try to install the Linux headers for your kernel version.
If this fails, what is the output of this on the terminal?
```
$ uname -r
```
[size=1]aptitude can be replaced with apt-get, but I suggest using the former since it seems to do a better job managing dependencies in my experience.[/size]

---

### Post by Ixtok72450 on 2006-01-08
Thanks for the quick answer, but still no go

I tried 
mark@ubuntu2:~$ sudo aptitude install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-headers-2.6.12-8-386"
The following packages have been kept back:
  evince libkpathsea3 libpoppler0c2 libpoppler0c2-glib linux-image-386
  linux-restricted-modules-386 mozilla-mplayer mozilla-openoffice.org
  openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-impress
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
  python-uno readahead-list sudo ubuntu-desktop ubuntu-docs xscreensaver
0 packages upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done



I tried   uname -r  and got:

mark@ubuntu2:~$ uname -r
2.6.12-8-386


thanks

Mark

---

### Post by duminas on 2006-01-08
Would upgrading your kernel break things beyond your ability to repair?
Header files for the newer kernel (2.6.12-10) exist in the Ubuntu repositories. Having searched, I cannot find any headers for your kernel, and do not know where you might find some. Upgrading your kernel would grant you access to header files in the official repositories, however.

If you would like to do so, you may need to change your sources.list a bit. Assuming you wish to try this and your sources.list allows it, do the following on the terminal:
```
$ sudo aptitude install linux-image-386 linux-restricted-modules-386
```This will install the most recent version of the 386 kernel it can find, as well as the restricted modules for that kernel (like nVidia modules and such, if I recall correctly). This will NOT, however, install the headers. I do it this way as it is easier to install them once you are under the newer kernel (or once you know the version it installed, at the least).

---

### Post by Ixtok72450 on 2006-01-08
Thanks,

That seems to have solved the kernel-headers problem. There are other issues with my attempted installation of Parallels-Workstation but I will email my questions to them.

Thanks
Ixtok

---

