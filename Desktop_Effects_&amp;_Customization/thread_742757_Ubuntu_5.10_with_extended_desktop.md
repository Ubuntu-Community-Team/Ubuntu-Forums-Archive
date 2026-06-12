---
title: "Ubuntu 5.10 with extended desktop"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by wieman01 on 2008-04-02
Sure it's Ubuntu 5.10? That version has run out of support, so you are unlikely to find much support here. Couldn't you go for the latest version (i.e. 7.10)?

---

### Post by K.Mandla on 2008-04-02
> **damd73 said:**
> I have Ubuntu 5.10 installed on my computer.  I have successfully installed the nVidia driver so I can use my gforce ti 4200 card.  To do that I followed method 2 from the following link:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Method 2 tell me to remove nVidia-glx.

When I restarted the computer, the graphics driver was a successful install.

I have 2 19" monitors connected to my gforce card but only 1 of them works.  I did a google and found the following link which tells you how to get twinview (which i am guessing means an extended desktop across 2 monitors) working.  I started to follow the instructions on the following page:

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

One of the first things this page says is to install nvidia-glx!  But I had to uninstall it when installing the drivers?  So I did it anyway and it broke my ubuntu install.  Therefore I ended up installing it again from scratch.

Now I have a brandnew install of ubuntu with the nvidia drivers 1.0.8756.

I have noticed that the nvidia-glx from synaptics is version 1.0.7667, which does not match my drivers.  I have also noticed after googling that nvidia-glx 1.0.8756 does exist.

Can anyone help me get an extended desktop working?

Thanks
Those are old drivers and much of that software has been updated. nvidia-glx used to be the core driver package for Nvidia cards, with nvidia-legacy (if I remember right) as the driver for outdated cards. The 4200 would probably have been one. 

I strongly recommend starting over with the freshest version -- 7.10, not the beta. Unless you're willing to wait a week or two and pick up 8.04 when it's released. 5.10 is, at this point, exceptionally old software.

---

