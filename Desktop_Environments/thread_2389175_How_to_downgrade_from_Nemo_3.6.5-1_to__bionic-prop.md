---
title: "How to downgrade from Nemo 3.6.5-1 to  bionic-prop Nemo?"
date: 2018-04-12
forum: Desktop Environments
---

### Post by Chanath on 2018-04-12
How to downgrade from Nemo 3.6.5-1 to  bionic-prop Nemo?

---

### Post by mc4man on 2018-04-12
Seeing as though you already have nemo installed it should be pretty simple  as all the other deps are installed.

First go here for a 64 bit install. You only want 1 package from under Built files, "libgnome-desktop-3-12_3.26.2-1ubuntu1_amd64.deb"
Download & install it with apt.
[https://launchpad.net/ubuntu/+source/gnome-desktop3/3.26.2-1ubuntu1/+build/13699536](https://launchpad.net/ubuntu/+source/gnome-desktop3/3.26.2-1ubuntu1/+build/13699536)

Then go here, you want some packages found in the drop downs for nemo & nemo-fileroller, the cinn. trans & xapp are ok on current bionic versions. No reason to add ppa as the needed packages are considered lower versions.
[https://launchpad.net/~mc3man/+archive/ubuntu/bionic-noprop/+packages](https://launchpad.net/~mc3man/+archive/ubuntu/bionic-noprop/+packages)
Get - 
libnemo-extension1_3.6.5-1~zzbionic_amd64.deb  
nemo_3.6.5-1~zzbionic_amd64.deb  
nemo-data_3.6.5-1~zzbionic_all.deb
nemo-fileroller_3.6.0-1~bionic_amd64.deb

Download all 4, put a an empty folder, cd to folder &
```
sudo dpkg -i *.deb
```
reboot & see if better.
If so,  for synaptic just pin those 4, I don't use apt to upgrade ever so that suffices just fine..

---

