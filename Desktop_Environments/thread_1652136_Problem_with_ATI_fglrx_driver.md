---
title: "Problem with ATI fglrx driver"
date: 2010-12-24
forum: Desktop Environments
---

### Post by Beamvr6 on 2010-12-24
Hi,

I have a few years old HP desktop with Ubuntu 10.10 and ATI Video. I can install fglrx using Synaptic and there all seems fine but nothing indicates the driver is really installed.

This is the info about the video:
```
~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)
```

After the installation fglrxinfo gives Segmentation fault, aticonfig gives aticonfig: No supported adapters detected. I've also run sudo dpkg-reconfigure xserver-xorg and rebooted multiple times.

/etc/X11/xorg.conf is there but empty. I've also been investigating Kernel Mode Setting but couldn't find something that works. I've tried this:

```

sudo nano /etc/default/grub.

Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.

Then sudo update-grub
```

So the string looked like GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" radeon.modeset=1. Update-grub returned /etc/default/grub: 9: radeon.modeset=1: not found.

I've been searching and trying for a couple of hours now. What do I need to do? Many thanks in advance.

---

### Post by clhsharky on 2010-12-24
Beamvr6

ATI's fglrx drivers only support HD-chips since 04-2009.

The default install (radeon) open source stack drivers, are the correct drivers for your Radeon 9200 card in Ubuntu 10.10.

Kernel Mode Setting can be checked in your Xorg.0.log, use your Log File Viewer.

What problems are you having?

Sharky

---

