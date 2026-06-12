---
title: "RemasterSys and proprietary drivers - Just want to know why"
date: 2009-01-09
forum: General Help
---

### Post by marriedman on 2009-01-09
I recently went on a distro hopping journey and a harrowing reinstallation of Kubuntu. I have never had such a hard time installing any OS before as the 10 different ones I tried these past 2 weeks.

It all started with my wanderlust getting the better of me. Ya know, just checking to see if the grass was any greener on the other side. I also wanted to try out KDE 4.2 and 64 bit support on my laptop. Long story short, Atheros wifi cards are the devil and multimedia keys on HP dv6700 series laptops are evil little gremlins.

That being said, I finally have Kubuntu 8.10 (32 bit though) with KDE 4.2 and third party drivers for my wifi and video. I don't want to go through all that I did again. So I started looking for a way to make my own recovery disc. I thought that I had found one in RemasterSys ( [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/) ). During my reading, I found that it does not keep any proprietary drivers when it makes the LiveCD and it is a limitation of Ubuntu. 

Does anyone know the reason behind this?

---

### Post by rbmorse on 2009-01-09
License language mainly. You aren't allowed to redistribute proprietary software without permission.

---

### Post by Fragadelic on 2009-01-21
The ubuntu livecd script set(casper) blacklists fglrx and nvidia kernel modules so you can't run them on the livecd.

I did try a few things way back but it was still kind of messed up which is probably why the devs blacklisted them.

There is also some rational thinking to not include a fixed xorg.conf and that is if your old pc dies and you get a new one, there is a chance the video might not be the same.  If the driver and xorg.conf was fixed from the original install, X would fail to start and you'd spend some time fixing that only to have to do the same on the install.

---

### Post by marriedman on 2009-01-21
Now that is an explanation and reason that makes perfect sense. I can now accept the reasoning. Thanks!

---

