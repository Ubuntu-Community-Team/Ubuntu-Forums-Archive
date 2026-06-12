---
title: "improper display after installing nvidia drivers"
date: 2012-07-27
forum: Desktop Environments
---

### Post by sid0972 on 2012-07-27
i have this motherboard

[gigabyte]("http://www.gigabyte.com/products/product-page.aspx?pid=2755#sp")

it has in built nvidia geforce 6150 graphics
it prompted me to install the additional nvidia drivers, so i did
after reboot, there was no launcher, not the menu on the top right (power options, and volume etc), just the folder i created on the desktop

i uninstalled them, came out fine

but it runs sort of slow, i havent turned on any effects (just some), but it takes its time
any ideas what can i do here?

---

### Post by bogan on 2012-07-27
Hi!, **sid0972**.

Did you ```
apt-get remove --purge nvidia*
``` ?? or just deactivate it?

Please Post:
```
cat /etc/lsb-release && uname -ar
apt-cache policy nvidia-current
apt-cache policy xserver-xorg-video-nouveau 
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!,** bogan.**

---

### Post by sid0972 on 2012-07-28
after deactivation the display is fine

its just i wanted to install the drivers, so that it runs smooth
anyways, i think i'll install my ATI card, should run fine then

---

