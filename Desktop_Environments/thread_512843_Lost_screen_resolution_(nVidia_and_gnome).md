---
title: "Lost screen resolution (nVidia and gnome)"
date: 2007-07-29
forum: Desktop Environments
---

### Post by jimhce on 2007-07-29
Hi,

I have a nVidia graphic card on gnome. When I start the PC, the screen resolution sometime was working fine, but sometime stuck on 640x480. When that happend, the system configuration for Screen Resolution displayed only 640x480, just like there was no driver for the nVidia card. Then I have to reboot, sometime several times to get the right resolution back. It is annoying, what could cause that problem and how can fix it?

Thank you.

Jim

---

### Post by pbcartwright on 2007-07-30
rty installing a package called 915resolution like this:
sudo apt-get install 915resolution

that should clear up your issues.. you do get the NVIDIA logo and it does load the NVIDIA driver, right??
if not, you need to download the nvidia driver first- go to nvidia.com and select download drivers for linux, and get the latest. Follow the instructions, read the README .

---

### Post by hammad1337 on 2007-07-30
also, you could try ```
sudo dpkg-reconfigure xserver-xorg
``` and specify resolution there.
or try manually editing /etc/X11/xorg.conf ```
sudo pico /etc/X11/xorg.conf
```

---

