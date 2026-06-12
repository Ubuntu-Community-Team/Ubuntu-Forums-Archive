---
title: "Broken X - nvidia drivers"
date: 2006-09-04
forum: Desktop Environments
---

### Post by hraposo on 2006-09-04
I've got a problem:
I installed the new nvidia drivers "NVIDIA-Linux-x86-1.0-8774-pkg1.run"
But now the X server is broken. The message is:
"Failed to initialize the nvidia kernel module!
The nvidia kernel module is version 1.0.7174
but this x module is version 1.0.7184."
I think that the problem is they are not the same version...
How I solve this problem?

---

### Post by hraposo on 2006-09-04
SOLVED!!! I don't need reinstall all from begin!

---

### Post by hraposo on 2006-09-04
SOLVED!!! I don't need reinstall all from begin!

---

### Post by sefs on 2006-09-04
Well don't keep us in anticipation.  Tell us the solution man.  The same thing happened to me and I had to reload from a backup image as I had no idea what to do.  That led to some other problems in itself.

So...what did you do to solve it.

Thanks.

---

### Post by hraposo on 2006-09-04
Just restore the nvidia drivers of ubuntu with this commands:
> sudo apt-get remove nvidia-glx linux-restricted-modules-$(uname -r)
sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx

---

### Post by codejunkie on 2006-09-04
> **sefs said:**
> Well don't keep us in anticipation.  Tell us the solution man.  The same thing happened to me and I had to reload from a backup image as I had no idea what to do.  That led to some other problems in itself.

So...what did you do to solve it.

Thanks.
to install the new nvidia drivers you have install these packages first
```
sudo aptitude install pkg-config xserver-xorg-dev build-essential linux-headers-`uname -r`
```
you also have to remove all restricted nvidia packages installed through synaptic with
```
sudo apt-get remove --purge nvidia*
```
now press ctrl+alt+F1 to switch to a terminal and kill the login manager with ```
sudo /etc/init.d/gdm stop
```
and run the nvidia installer.

---

### Post by sefs on 2006-09-04
Brilliant!!! 

Thanks a mil.

> **codejunkie said:**
> to install the new nvidia drivers you have install these packages first
```
sudo aptitude install pkg-config xserver-xorg-dev build-essential linux-headers-`uname -r`
```
you also have to remove all restricted nvidia packages installed through synaptic with
```
sudo apt-get remove --purge nvidia*
```
now press ctrl+alt+F1 to switch to a terminal and kill the login manager with ```
sudo /etc/init.d/gdm stop
```
and run the nvidia installer.

---

### Post by sefs on 2006-09-04
Quick question...
I am getting some dependancies errors when trying to install the xorg server dev package (related to libdrm ect, then when i try to install that sepearately that leads to more dependances not found errors) in synaptic and i suspect my repos may not be complete which ones should i have to work for this.

my sources.list

```

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://archive.canonical.com/ubuntu dapper-commercial main
# deb http://xgl.compiz.info/ dapper main
# deb http://www.beerorkid.com/compiz dapper main
# deb http://media.blutkind.org/xgl/ dapper main
# deb http://ubuntu.compiz.net/ dapper main

```

---

### Post by claude05 on 2006-09-04
Sorry I am a complete noob at this once I write "sudo /etc/init.d/gdm stop" and switch to the terminal what code do I have to write to run the installer?
I have the NVIDIA-Linux  pkg1.run file on my desktop by the way.

---

### Post by codejunkie on 2006-09-04
> **claude05 said:**
> Sorry I am a complete noob at this once I write "sudo /etc/init.d/gdm stop" and switch to the terminal what code do I have to write to run the installer?
I have the NVIDIA-Linux  pkg1.run file on my desktop by the way.

cd to the directory where the installer is, and enter **sh NVIDIA** and hit the tab key and it will autofill in the rest then hit enter and it will start the installer.

---

