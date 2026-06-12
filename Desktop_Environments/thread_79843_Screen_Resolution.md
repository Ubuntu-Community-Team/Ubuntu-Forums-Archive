---
title: "Screen Resolution"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Raul Fuenzalida on 2005-10-20
I have a monitor which support the following resolutions:

VGA 600 x 400 @ 70 Hz
VGA 640 x 480 @ 60 Hz
VESA 640 x 480 @ 75, 85 Hz
VESA 800 x 600 @ 75, 85 Hz
VESA 1024 x 769 @ 85 Hz
VESA 1280 x 1024 @ 60 Hz

I've just installed Ubuntu, and it shows me a 640x480px screen.. I went to screen resolution options, and it only gives me one option: 640x480px at 60Hz.

I would like to set up the screen resolution with 1280x1024px, with 32bit color and I don't know how to do that. Please, can someone explain me? thanks

---

### Post by migueljacq on 2005-10-20
[QUOTE=Raul Fuenzalida]I have a monitor which support the following resolutions:

VGA 600 x 400 @ 70 Hz
VGA 640 x 480 @ 60 Hz
VESA 640 x 480 @ 75, 85 Hz
VESA 800 x 600 @ 75, 85 Hz
VESA 1024 x 769 @ 85 Hz
VESA 1280 x 1024 @ 60 Hz

I've just installed Ubuntu, and it shows me a 640x480px screen.. I went to screen resolution options, and it only gives me one option: 640x480px at 60Hz.

I would like to set up the screen resolution with 1280x1024px, with 32bit color and I don't know how to do that. Please, can someone explain me? thanks[/QUOTE]


Go to your terminal and type dpkg-reconfigure xserver-xorg (possibly sudo, can't remember) and configure your resolution settings from there.

---

### Post by jeffreyvergara.NET on 2005-10-20
i did mine with sudo, "sudo dpkg-reconfigure xserver-xorg" just read it carefully and you will be all set.

---

### Post by aysiu on 2005-10-21
This page may be helpful:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

