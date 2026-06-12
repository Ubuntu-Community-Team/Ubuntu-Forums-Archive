---
title: "Gnome Freezes After resume from sleep."
date: 2013-06-16
forum: Desktop Environments
---

### Post by raidflex on 2013-06-16
I have an Asus ux32VD laptop with Ubuntu Gnome 13.04 and I have an issue with the Gnome desktop freezing when resuming from sleep. When it resumes I would see the desktop background and icons and I can move the mouse, but nothing is responsive.  I find that the system does not freeze every time. I can drop to the command line and restart GDM and it is fine. 

I also have done a complete re-install of Ubuntu Gnome 13.04. with the same issue. Please advise. Thanks.

---

### Post by kurt18947 on 2013-06-16
> **raidflex said:**
> I have an Asus ux32VD laptop with Ubuntu Gnome 13.04 and I have an issue with the Gnome desktop freezing when resuming from sleep. When it resumes I would see the desktop background and icons and I can move the mouse, but nothing is responsive.  I find that the system does not freeze every time. I can drop to the command line and restart GDM and it is fine. 

I also have done a complete re-install of Ubuntu Gnome 13.04. with the same issue. Please advise. Thanks.

It appears your notebook uses Nvidia graphics.  Is this an Optimus chipset? I don't know how your machine will react to what I'm going to suggest.  I'm using a 5 year old desktop with AMD processor/chipset & Nvidia graphics.  I was having the same suspend/resume issue and traced it to the video driver.  The open source driver and Nvidia's 304 driver cause the same symptons as you're experiencing.  I installed Nvidia's 319 experimental drivers and so far so good.  This is with 13.10.  I was using Nvidia's 310 on 13.04 and the 310 series fixed the problem as well.

---

### Post by raidflex on 2013-06-16
> **kurt18947 said:**
> It appears your notebook uses Nvidia graphics.  Is this an Optimus chipset? I don't know how your machine will react to what I'm going to suggest.  I'm using a 5 year old desktop with AMD processor/chipset & Nvidia graphics.  I was having the same suspend/resume issue and traced it to the video driver.  The open source driver and Nvidia's 304 driver cause the same symptons as you're experiencing.  I installed Nvidia's 319 experimental drivers and so far so good.  This is with 13.10.  I was using Nvidia's 310 on 13.04 and the 310 series fixed the problem as well.

I have the NVIDIA 319 drivers with bumblebee for Optimus, it may be something else.

---

### Post by raidflex on 2013-06-17
Anyone have any other ideas? Could a shell extension cause the problem? Its hard when i cannot duplicate the issue every time, it seems to happen more after the computer has been idle and goes to sleep on its own. I also noticed that sometimes gnome will not freeze up completely, but would become responsive after 15 seconds or so and then I could unlock the laptop.

---

### Post by kurt18947 on 2013-06-17
> **raidflex said:**
> Anyone have any other ideas? Could a shell extension cause the problem? Its hard when i cannot duplicate the issue every time, it seems to happen more after the computer has been idle and goes to sleep on its own. I also noticed that sometimes gnome will not freeze up completely, but would become responsive after 15 seconds or so and then I could unlock the laptop.

Possibly.  Maybe install Xfce or LXDE?  I think if you don't install the Xfce or LXDE desktop you won't get the alternative apps that come with those desktops.  Switch to one of the other desktops, suspend and see what happens.

---

