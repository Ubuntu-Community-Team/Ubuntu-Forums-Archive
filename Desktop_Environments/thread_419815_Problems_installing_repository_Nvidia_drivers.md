---
title: "Problems installing repository Nvidia drivers"
date: 2007-04-23
forum: Desktop Environments
---

### Post by knockturnx on 2007-04-23
Ok i have a Geforce 7800GS [agp] card and when installing the packages through synaptic or apt-get and i restart, xserver crashes compleatly and wont load back up again. Any ideas?

---

### Post by beerorkid on 2007-04-23
well to at least get your GUI up again you can edit your xorg.conf

so when you boot up and get the X crash error login (might have to alt + ctrl + F1

sudo vi /etc/X11/xorg.conf

and change the video driver to "vesa"

example:

```
Section "Device"
        Identifier      "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "vesa"
        BusID           "PCI:1:0:0"

```

then you can try to install the driver again.

There is the restricted drivers manager although I have not tried them.
system --> administration --> restricted driver manager

I have had very good luck with the [envy script]("http://www.albertomilone.com/nvidia_scripts1.html") in the past.  I find it is better to install in the alt + ctrl + F1 tty though.

---

