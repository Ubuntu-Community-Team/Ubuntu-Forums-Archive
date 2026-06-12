---
title: "Dell Latitude D610 screen resolution"
date: 2008-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BekeTom on 2008-06-23
I have Dell Latitude D610. I'm using Ubuntu through VirtualBox. Ubuntu appear only in 600X800 resolution. I would like to install some driver, but I don't know how and when can I find the right driver.

I have Mobile Intel(R) 915GM/GMS, 910GML Express Chipset Family display adapter.

I'm absolutely beginner concerning Linux

Is there any suggestion.

thx

---

### Post by cacycleworks on 2008-06-23
> **BekeTom said:**
> I have Dell Latitude D610. I'm using Ubuntu through VirtualBox. Ubuntu appear only in 600X800 resolution. I would like to install some driver, but I don't know how and when can I find the right driver.

I have Mobile Intel(R) 915GM/GMS, 910GML Express Chipset Family display adapter.

I'm absolutely beginner concerning Linux

Is there any suggestion.

thx

Hi and Welcome!

I don't know anything about virtual box ... did you try booting to the live CD? This is admittedly slow, but if you boot with your expected resolution, you can copy the /etc/X11/xinitrc file to usb stick or to local harddrive and then try that in virtual box ???

The xinitrc says the driver to use as well as the various settings... once you have a xinitrc that works, this is key for forward use should anything break with other installs or versions.

You can also try a dpkg-reconfigure xorg, but I believe in Hardy, they removed the opportunity to manually choose a driver. :( 

I suggest searching whatever you can about video setup and resolution. Or maybe someone will see this who has experience solving that problem. 

:) Chris

---

