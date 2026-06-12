---
title: "Use Kubuntu CD to install without downloading for Ubuntu?"
date: 2007-06-26
forum: Desktop Environments
---

### Post by kargath64 on 2007-06-26
I have just gotten the Feisty Kubuntu 64 and Ubuntu 64 discs, and have successfully installed Ubuntu.  However, I also want the KDE desktop installed on my system.  I wish to use the Kubuntu CD to install the kubuntu-desktop package instead of waiting two days solid on the internet for the metapackage to download its components.  Any way this can be done?
I've already tried inserting the Kubuntu disc.  It's recognised as a source disc and Synaptic opens up and everything, but when I click the Origin button and select the Kubuntu disc, all that is present is a small collection of network/ISDN utilites.  Trying to install kubuntu-desktop package with the Kubuntu CD in the tray just tries to download from the 'net.

---

### Post by orb9220 on 2007-06-27
Did you add the cdrom to your repositories in synaptic?

---

### Post by kargath64 on 2007-07-04
AFAIK, yes.  I mean, the dialog "An Ubuntu CD has been detected" popped up and everything, plus it seems to be in my list of sources in Synaptic. 
Clicking on either of those "Kubuntu CD" sources just lists a tiny amount of non-KDE packages.  Not what I'm looking for.

---

### Post by sosy on 2007-07-04
hey,
I have the same problem. I don't have an internet connection at home so my only option is  the cd. for some reason, all kde related packages are not shown even if u have a kubuntu cd.

---

### Post by scxtt on 2007-07-04
post the output of:

cat /etc/apt/sources.list

and familiarize yourself w/ the program **apt-cdrom**:
```
apt-cdrom is used to add a new CDROM to APTs list of available
       sources.  apt-cdrom takes care of determining the structure of the
       disc as well as correcting for several possible mis-burns and
       verifying the index files.
```

---

### Post by sosy on 2007-07-05
here's the content of /etc/apt/sources.list ...
I've excluded all the comments

> deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
**deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted**

---

### Post by scxtt on 2007-07-05
looks like it's using the cd as a repo ...  but i popped my feisty kubuntu disk in, and i only see a few .debs - it doesn't seem like you can install a kubuntu desktop from it :( - unless it has its own special way of doing it - or it's because i have a LiveCD - maybe it'd work off an alternate disk?
```
./pool/main/b/bpalogin/bpalogin_2.0.2-9ubuntu1_i386.deb
./pool/main/b/build-essential/build-essential_11.3_i386.deb
./pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb
./pool/main/e/eagle-usb/eagle-usb-data_2.1.1-2.1ubuntu1_all.deb
./pool/main/e/eagle-usb/eagle-usb-utils_2.1.1-2.1ubuntu1_i386.deb
./pool/main/f/fakeroot/fakeroot_1.5.10ubuntu2_i386.deb
./pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb
./pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb
./pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb
./pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb
./pool/main/i/isdnutils/capiutils_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/ipppd_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/isdnutils-base_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/isdnutils-xtools_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/libcapi20-3_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/libcapi20-dev_3.10.20070306-0ubuntu1_i386.deb
./pool/main/i/isdnutils/pppdcapiplugin_3.10.20070306-0ubuntu1_i386.deb
./pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb
./pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_i386.deb
./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.6+svn20061108-2ubuntu1_i386.deb
./pool/main/m/mouseemu/mouseemu_0.15-6ubuntu5_i386.deb
./pool/main/p/pptp-linux/pptp-linux_1.7.0-2ubuntu2_i386.deb
./pool/main/s/setserial/setserial_2.17-43_i386.deb
./pool/restricted/d/drdsl/drdsl_1.2.0-1_i386.deb
./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.20.15.14_i386.deb
./pool/restricted/l/linux-restricted-modules-2.6.20/avm-fritz-firmware-2.6.20-15_3.11+2.6.20.5-15.20_i386.deb

```

---

### Post by Canis familiaris on 2007-07-05
You CANNOT install the kubuntu-desktop package using the LIVE CD.
However you can using the alternate CD:
1) Add the CD-ROM to your repository
```
sudo apt-cdrom -m add
```
2) DIsable other repositories. Go to System->Administration->Software Sources and disable all the Ubuntu repos.
3) Now update your database
```
sudo apt-get update
```
4) Now install kubuntu-desktop package:
```
sudo aptitude install kubuntu-desktop
```

---

### Post by Canis familiaris on 2007-07-05
And YES do not forget to re enable the repos you had previously disabled as well.

---

### Post by sosy on 2007-07-05
i'm a little bit confused :confused:. the shipIt cd, u can use it as a live cd and as an install cd. so what exactly is an alternate cd?

---

### Post by scxtt on 2007-07-05
the alternate cd is a less resource intensive install disk - basically the old ncurses display ... i'm thinking the LiveCD "copies" the live image onto your hard drive whereas the alternate disk does more of a *dpkg -i $package* install - making it more suited to install packages from ...

---

### Post by kargath64 on 2007-07-05
damn.  that's really, really annoying.
there so should be a warning about this on the download page.

---

### Post by scxtt on 2007-07-05
why?, the disk isn't intended to be used as a repo to install KDE - it's intended to be used as a LiveCD/install disk ...

---

