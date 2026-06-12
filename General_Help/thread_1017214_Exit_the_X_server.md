---
title: "Exit the X server?"
date: 2008-12-20
forum: General Help
---

### Post by lander2k2 on 2008-12-20
I'm tying to install an Nvidia driver and it requires that I exit the X server.

Can anyone explain how to do this?

Thx

---

### Post by snova on 2008-12-20
Press Ctrl-Alt-F1 to get to a terminal. Login, and run this:

```
sudo /etc/init.d/gdm stop
```

Which will stop X, GDM, Gnome, and all the rest.

On the other hand, if you just need to restart X, press Ctrl-Alt-Backspace.

---

### Post by 3rdalbum on 2008-12-20
If you haven't already, you should try the Hardware Drivers program included with Ubuntu, to install the Nvidia driver. Disregard if you've already tried and it hasn't worked.

---

### Post by dcstar on 2008-12-20
> **3rdalbum said:**
> If you haven't already, you should try the Hardware Drivers program included with Ubuntu, to install the Nvidia driver.

Installing non-repository Nvidia drivers can cause problems whenever there is a kernel update, as this usually requires a recompile/reinstallation of the driver.

As a general rule, it is far better to use the Ubuntu driver as it is updated whenever the kernel is updated and your system will keep on working.

---

### Post by zek725 on 2008-12-20
> **dcstar said:**
> Installing non-repository Nvidia drivers can cause problems whenever there is a kernel update, as this usually requires a recompile/reinstallation of the driver.

As a general rule, it is far better to use the Ubuntu driver as it is updated whenever the kernel is updated and your system will keep on working.

How do I do that? How do I install the Ubuntu-release video driver? I am confused with **nv** and **nvidia**. I used to have an nvidia driver in my *Hardware Drivers* but now I don't have one. Does it have to do something with upgrading? I am unaware if my sister upgraded something or if it was me, but I have a Samsung SyncMaster 931BW. Upon logging in to the system, the display is in low graphics mode and was prompted to configure the drivers to display higher resolutions. The LCD widescreen panel is connected using a DVI. 

I installed Ubuntu and the display was plug-n-play-fine. I remember activating the Nvidia driver once to utilize the Compiz desktop effects and now I am unable to enjoy the wobbling windows, and other desktop effects. :(

Video Card: nVidia GeForce FX 5500. 256 MB RAM

---

