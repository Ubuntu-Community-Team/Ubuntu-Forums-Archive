---
title: "Virtualbox guest addons"
date: 2009-01-10
forum: General Help
---

### Post by kutlu on 2009-01-10
I want to use any ubuntu (or linux) distro under Virtualbox.

I tried on Kde4, I had problems with guest add-ons.
I installed Virtualbox guest addons by running the executable with sudo as some topic in this forum suggests. It gave something like "X window sysyem is not recognized". Nothing about addons work.

Should I try any other distro without kde4? I previously installed addons on Pardus(kde3) using this method, It gave error about not recognition of distro, but it worked except window resizing.

I don't know if it is because kde4, but should I better install addon from repository?
Is there any in repository?

---

### Post by namdung on 2009-01-10
I have Kubuntu, Xubuntu etc. installed using Virtualbox with guest addons installed.

Which Ubuntu version as Host?
Which version of Virtualbox?
How are u trying to install the addons?

---

### Post by kutlu on 2009-01-10
host: debian
guest: xubuntu (I've just tried.) or kubuntu

It gives: "unknown version of the X window system installed"

it works perfect when xp is guest, works somehow when pardus is guest.
But it does not work with xubuntu or kubuntu

I installed it from "Devices->install guest addons" of virtualbox

---

### Post by namdung on 2009-01-10
This is how I do it in Ubuntu 8.04.1 using Virtualbox 2.0.6

First ensure that the **VBoxGuestAdditions.iso** is selected in the *CD/DVD* settings. 
Boot the System.
Inside Guest OS open terminal.
```
cd /media/cdrom0
```
*cdrom0* is usually where the *VBoxGuestAdditions.iso* is mounted. Change this if required.
Type ```
ls
``` to see all addon files listed.
To install ```
sudo ./VBoxLinuxAdditions-x86.run
```

The current Virtualbox version is 2.1.0.

---

### Post by kutlu on 2009-01-10
I did the same thing. Does not work on mine.
It seems that X version of Xubuntu and kubuntu is not compatible with Virtualbox installation.
any ideas?

Does Anyone has one of xubuntu or kubuntu kde4 under Virtualbox?

---

### Post by kutlu on 2009-01-10
Problem is that, I am using Virtualbox 1.6.6. :S, so, new X window is not supported by my Virtualbox.

---

### Post by namdung on 2009-01-10
> **kutlu said:**
> Problem is that, I am using Virtualbox 1.6.6. :S, so, new X window is not supported by my Virtualbox.

Pls install the current version (2.1.0)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Don't worry, ur old virtual machines will not be deleted.
Manual here
[http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf)

---

### Post by ashraful on 2009-01-10
Hi
I am using Dell Inspiron 6400. Installed Ubuntu hardy and vituralbox 1.6.6
When I run WinXP in vitualbox, I can hear sound but cannot record. I am using pulseAudio driver and ICH AC97 controller. In winxp it show Intel Integrated sound driver. I try to use voip software freecall in windows, it cant play or record sound as it gets Intel sound card from device driver. But window media player can play sound and it output to directsound device.

And can anybody say how can I start a new Thread in ubuntu forum?

Thanks,
Ashraf

---

