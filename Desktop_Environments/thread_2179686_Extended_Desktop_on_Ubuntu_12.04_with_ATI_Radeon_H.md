---
title: "Extended Desktop on Ubuntu 12.04 with ATI Radeon HD8570"
date: 2013-10-09
forum: Desktop Environments
---

### Post by deepthought365 on 2013-10-09
I just bought a 64-bit Dell Optiplex 9020 and was excited to install Ubuntu 12.04 on it. I have two monitors and extended desktop support works fine with my ATI Radeon HD8570 video card on Windows 7. However, after installing Ubuntu 12.04, it recognizes both monitors as only one labelled "Laptop" and simply mirrors my desktop on each. The option to uncheck "Mirror monitors" is also grayed out. I have looked online and tried everything I can to get extended desktop support but I can't seem to figure it out. I tried to install the Catalyst drivers from the ATI website and it simply says my video card is not supported.

What do I do? I'd really appreciate any help.

---

### Post by SCBrisbane on 2013-10-14
Hi,
I also cannot add multiple monotors, and I always see a single display, labelled as 'laptop', no matter which of the 4 video ports I plug the monitors in to on the back.  Again, this is a Optiplex 9020 and 12.04.  In addition I cannot change the resolution.  

Interestingly, [http://www.ubuntu.com/certification/hardware/201302-12847/](http://www.ubuntu.com/certification/hardware/201302-12847/) says the hardware is certified for use with Ubuntu 12.04.2, though it has some reference to vendor customization of the install. Can we get acces to these customizations?

For anyone else reading this, I also had to change the kernel to 3.5 (or later) to get the network  card working (the v3.5/quantal was released around the time of 12.04.2).

---

### Post by karud on 2013-10-16
I had the same problem with ubuntu 13.04 64-bit. Just installed as root the latest beta driver from AMD
[http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)
[http://www2.ati.com/drivers/beta/amd-catalyst-13.11-betav1-linux-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.11-betav1-linux-x86.x86_64.zip)
It works fine now after reboot. You may find the better way though.

---

