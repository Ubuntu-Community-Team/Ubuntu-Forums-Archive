---
title: "funny business with dual-head setup"
date: 2009-11-21
forum: Desktop Environments
---

### Post by denarced on 2009-11-21
This one seems like a hard one so if you guys don't know the answer and can't even guess then just throw stuff at me: error logs, logs, diagnostic tools, what ever

So I have dual head setup with nvidia GTX-275 and 9.04 Jaunty with all the latest updates and Xorg X Server 1.6.0

Here's what happens:
[INDENT]Normally when I start and login screen appears, it's on the left monitor. On the occasion, the left screen is blank and gets no signal AND the login-GUI does not appear on the right screen.
If I do this login blind like most of us can do in our sleep:D, the monitor never lights up.
This problem bugs me :x.

I check Xorg logs from /var/log, compared one from 'doesn't work'-startup to a working startup => no difference[/INDENT]

So what could it be ??

Much thanks to all you knowing people

---

### Post by gradinaruvasile on 2009-11-21
What driver version u have?
I suggest going to the Nvidia site and download/install the latest linux driver there (190.42 i think).

---

### Post by denarced on 2009-11-21
> **gradinaruvasile said:**
> What driver version u have?
I suggest going to the Nvidia site and download/install the latest linux driver there (190.42 i think).

I have 180.44

Don't you have to then reinstall every time you upgrade kernel ?

---

### Post by gradinaruvasile on 2009-11-21
No if its the stock driver.
Or if u get it from this PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

In a terminal:

sudo gedit /etc/apt/sources.list

add

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

to the end of the list, save,close.

Then update from update manager.
Then install 
nvidia-glx-190
nvidia-190-libvdpau
nvidia-190-modaliases

packages. Then reboot.

---

### Post by denarced on 2009-11-22
> **gradinaruvasile said:**
> No if its the stock driver.
Or if u get it from this PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

In a terminal:

sudo gedit /etc/apt/sources.list

add

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

to the end of the list, save,close.

Then update from update manager.
Then install 
nvidia-glx-190
nvidia-190-libvdpau
nvidia-190-modaliases

packages. Then reboot.

sounds like worth a shot .. thanks

---

