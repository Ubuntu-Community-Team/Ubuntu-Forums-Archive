---
title: "Driver in Linux for a cable modem"
date: 2009-02-26
forum: General Help
---

### Post by e.jejcic on 2009-02-26
Dear Sirs.:
I wonder where I can download a driver in Linux (Ubuntu 8.10) for a cable modem from scientific atlanta DPC2100.
Thanks in advance. Eduardo.

---

### Post by mb_webguy on 2009-02-26
I've never seen an internal cable modem, and if it's an external cable modem connected by an Ethernet cable, no driver should be required.

---

### Post by SoCalChris on 2009-02-26
I looked up the model # that you included, and see that the modem has both a USB and ethernet connector. Can you just disregard the USB, and connect it to your computer with the ethernet? You shouldn't need a driver that way.

---

### Post by e.jejcic on 2009-03-02
Thanks to mb_webguy and SoCalChris for54 the response. I appreciate it.I am waiting for the finishing of my warranty ( it is a new computer) to peep inside for the ethernet card.
Thanks,  Eduardo.

---

### Post by binbash on 2009-03-02
I am using cable modem since 1999 on linux systems, i never ever heard a modem driver :D .Just plug the ethernet cable in if it does not a wireless cable modem.

---

### Post by fragos on 2009-03-03
> **binbash said:**
> I am using cable modem since 1999 on linux systems, i never ever heard a modem driver :D .Just plug the ethernet cable in if it does not a wireless cable modem.

Same here. If your setup is DCHP for IP and DNS all works without a hitch. Even sticking a wireless router between the PC and the cable modem still works unless your ISP blocks on MAC address. In that case you just need to tell the router to clone your PC's MAC.

---

### Post by James- on 2009-03-03
Drivers are available threw kernel compiling...You can always add drivers afterwards but it's a pain in the ***. You can try compiling a beta kernel

**Note this may solve the driver problem or it might not(because either the driver is not enabled by default(meaning you have to go through menuconfig and enable it) or it is not supported**
How to upgrade your kernel:
**Most of the commands are in the terminal to simplify the instructions**
A few tools that you will need:
> 
apt-get update
apt-get install build-essential git-core kernel-package libncurses5-dev fakeroot bzip2 wget zlib1g-dev

Give your user access to the src folder, replace your_username with the obvious
> 
adduser your_username src

Log out entirely (ctrl+d in the terminal, and log out of X too if you are in the GUI) and log back in again with your regular user account. You will now have write permission on /usr/src.

Now get the new kernel source tarball (2.6.29rc6 as of my last edit):
> 
cd /usr/src
wget [http://kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.29-rc6.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.29-rc6.tar.bz2)
tar jxvf linux-2.6.29-rc6.tar.bz2
cd linux-2.6.29-rc6
make oldconfig
make menuconfig

[b]
Note in menu config press esc twice to accept defaults
Also that holding down enter in oldconfig during is generally safe to accept defaults
[/b]
[b]If you have a Dual-Core or a Quad-Core the compilation process will be accelerated if you run the fallowing command:
[/b]
> export CONCURENCY_LEVEL=xxxxx
Replace xxxxx with the number of cores you have DualCore(2) AMDX3(3) Quad(4)

To compile:
> 
fakeroot make-kpkg --initrd kernel_image kernel_headers


After that finishes(might take a while), install your new kernel and kernel headers. As root:
> 
cd ..
dpkg -i linux-image-2.6.29-rc6_2.6.29-rc6-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.29-rc6_2.6.29-rc6-10.00.Custom_i386.deb


reboot:
> 
shutdown -r now


---

