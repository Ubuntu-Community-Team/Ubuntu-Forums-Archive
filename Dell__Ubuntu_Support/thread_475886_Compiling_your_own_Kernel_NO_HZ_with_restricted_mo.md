---
title: "Compiling your own Kernel: NO_HZ with restricted modules."
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by neptho on 2007-06-16
This is a simple little introduction to how I got my aging Inspiron 6400 to run a recent kernel with the NO_HZ configuration, and the default debugging symbols to make it [PowerTop Statistics](http://www.linuxpowertop.org/) friendly.

I have a Centrino Duo (Not Core 2) 1.6Ghz system with the ATI x1300 video, and the Intel 3945 802.11g/a card.  *Unless you are running the same hardware, following these instructions to the tee, without modifications for your own hardware will likely mean that you'll probably lose your wireless support, at the least!*

*I strongly suggest you only do this if you are comfortable with Linux, the shell, and know how to recompile/reinstall the restricted drivers base*; the newer code merits more use for me, so that's how I'm doing my own thing.  ;)

Please note that a '%' just means 'open a terminal, and run this as your own user', don't type the '%'. '#' means you are running as the 'root' user.  Be verrry careful, you can really mess things up as root!

First, let's get the latest Ubuntu kernel sources, the debian (and Ubuntu developer) way:

```
%sudo $SHELL
#cd /usr/src
#apt-get install wget
#wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-6.13.dsc
#wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-6.13.tar.gz
```

Ok, now that's make sure we have what we need to have, to build a kernel, and put everything into place:

```
#apt-get build-dep linux-image-generic build-essential dpkg-source
#dpkg-source -x linux-source-2.6.22_2.6.22-6.13.dsc
#ln -sf linux-source-2.6.22-2.6.22 linux
#cd linux
#cp /boot/config-2.6.20*generic .config
```

I have an X1300 and the Intel 3945, so I need to rebuild for my new kernel.  I'd better have the code before the machine's 'down and out!

First, the latest ATI binary driver:

```
#cd /usr/src
# mkdir ati; cd ati; wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.37.6-x86.x86_64.run
#bash *run --buildpkg Ubuntu/Feisty
#dpkg -i *.deb
```

Now, the IPW3945 driver (I'd like to switch to the later ipwifi, but that's far too much effort for this tutorial):
```
#cd /usr/src;mkdir ipw3945; cd ipw3945
# wget 'http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.1.tgz?download'
# tar zxvpf ipw3945-1.2.1.tgz
```

Ok, so we have our 'safety net'.  Let's build the kernel.  First, let's run through the new options.  It's generally safe to chose the defaults.  Usually.  Make sure you pay attention, though.  Turn off IRQBALANCE and any modules you won't need.  It'll make compile time faster.

```
#cd /usr/src/linux; make oldconfig
```

Now, this is going to take forever.  This was my SECOND build attempt (the first worked, but I forgot something, so I needed to start over.
```
#cd /usr/src/linux
#make-kpkg clean
#make-kpkg --append-to-version=-2-686-generic --initrd kernel_image kernel_headers
```

First, install the kernel headers.  If this fails, we won't be able to make new modules.
```
#cd /usr/src
#dpkg -i linux-headers-2.6.22-rc3-2-686-generic_2.6.22-6.13_i386.deb
```

All worked?  Ok, let's install the kernel.  Wait, we don't have support for the firmware, so let's copy that, first.  There's a better way, but this is fast and rogue.  ;)

```
#cp -R /lib/firmware/`uname -r` /lib/firmware/2.6.22-rc3-2-686-generic
```

Now, let's install the kernel:

```
#dpkg -i linux-image-2.6.22-rc3-2-686-generic_2.6.22-6.13_i386.deb
```

Ok, let's reboot into our new kernel.  When the system starts and askes 'Press Esc' for grub menu, press 'Esc', and choose the second option (2.6.22 Recovery Mode).

Let it boot, and when it prompts for the password, enter your password.

Let's make sure all partitions are mounted:
```
#mount -a
```

Ok, let's install fglrx:

```
#cd /usr/src; bzip2 -dc fglrx.tar.bz2 | tar xvpf - -C /usr/src/ati
#cd /usr/src/ati/modules/fglrx
#bash make.sh
#mkdir /lib/modules/`uname -r`/misc
#cp fglrx.ko /lib/modules/`uname -r`/misc
#depmod -ae
#modprobe fglrx
```

Check to see if it loaded:
```
#dmesg | tail -5
```

This is a bit strange how Ubuntu does this: Binaries are tagged by kernel revision for support modules too.  Er, OK.  Let's copy the ipw3945 daemon over to this kernel version; we don't need to recompile (Exchange 2.6.20-15-generic with your prior kernel version.  It's probably easiest to just type ipw3945d- then press tab.):

```
#cp /sbin/ipw3945d-2.6.20-15-generic /sbin/ipw3945d-`uname -r`
#cd /usr/src/ip3945/ipw3945-1.2.1
#make
#make install
```

Finally, test to see that the ipw3945 driver works:
```
#modprobe ipw3945
```

If you get an error about not finding /sbin/ipw3945d-kernelversion, you either typo'd, for forgot to copy the ipw3945 daemon, above.

Now, this is somewhat divergent from Ubuntu's basic kernel version, but it's trivial to 'fall back'.  If it doesn't work, or you really want to go back, you can press 'ESC' at boot time, choose an older kernel, then 
```
apt-get --purge remove linux-headers-2.6.22\* linux-image-2.6.22\*
```

if you installed the updated ATI driver, you can reinstall the elder version with:
```
apt-get --reinstall install xorg-driver-fglrx linux-restricted-modules-2.6.20-16-generic
```

---

### Post by Beefeater on 2007-06-19
Cheers mate. Beautiful.

---

### Post by FloSynergy on 2007-06-19
ok, this seems very easy to follow.
my problem has to do with hardware recognition - i have posted it [here.]("http://ubuntuforums.org/showthread.php?t=478163")

as a result, i am starting to think that it may be more effective for me to install a new kernel.

But:
Since I have no LAN access (it's an on-board LAN chip and not recognised, right?), there seems to be no way to run anything like apt-get, etc.

any suggestions?

in keen anticipation,

Flo.

---

### Post by neptho on 2007-06-19
Hi Flo,

Unless you can download to another system to a USB flash drive, or burn a CD, there's relatively few ways to get the kernel onto that machine.  I have found no documentation in 2.6.22 regarding support of the RealTek 8201cl; it may not be supported, yet.

You can always try 'ndiswrapper', but I have no idea how well (if at all) that will function.  I've only seen it used exclusively with wireless cards.

---

### Post by Beefeater on 2007-06-19
> **FloSynergy said:**
> ok, this seems very easy to follow.
my problem has to do with hardware recognition - i have posted it [here.]("http://ubuntuforums.org/showthread.php?t=478163")

as a result, i am starting to think that it may be more effective for me to install a new kernel.

But:
Since I have no LAN access (it's an on-board LAN chip and not recognised, right?), there seems to be no way to run anything like apt-get, etc.

any suggestions?

in keen anticipation,

Flo.

You don't have an old PCI network card lying around that you can try with?

---

### Post by FloSynergy on 2007-06-20
ok,

well, I've been using my pleistocene laptop to surf the net and post these comments, so i can access the net to download stuff. i'm just not sure how to locate, download and install all the necessary packages without using synaptic - will the repositories allow me to simply download packages to a folder which i can copy to a flash disk? as for ndiswrapper, i have tinkered around with that a little, but with the resulting feedback that the relevant driver is already installed...go figure!

with regard to an old pci card to plug in, i'm afraid I have nothing suitable floating about my mulch-pit of an office... ;-)

ok, 
i'll see if i can figure out how to get hold of the missing packages...

thanks for your responses,

be well,

flo

---

### Post by prince_niceguy on 2007-07-26
thanks for the info... was able to upgrade my kernel to 2.6.22 without issues.

A caution note though if you are using bash shell and trying to install ipw3945 then use the following command

> make SHELL=/bin/bash

thanks again!!!

---

### Post by kill4killin on 2007-11-21
> **neptho said:**
> This is a simple little introduction to how I got my aging Inspiron 6400 to run a recent kernel with the NO_HZ configuration, and the default debugging symbols to make it [PowerTop Statistics](http://www.linuxpowertop.org/) friendly.

I have a Centrino Duo (Not Core 2) 1.6Ghz system with the ATI x1300 video, and the Intel 3945 802.11g/a card.  *Unless you are running the same hardware, following these instructions to the tee, without modifications for your own hardware will likely mean that you'll probably lose your wireless support, at the least!*

*I strongly suggest you only do this if you are comfortable with Linux, the shell, and know how to recompile/reinstall the restricted drivers base*; the newer code merits more use for me, so that's how I'm doing my own thing.  ;)

Please note that a '%' just means 'open a terminal, and run this as your own user', don't type the '%'. '#' means you are running as the 'root' user.  Be verrry careful, you can really mess things up as root!

First, let's get the latest Ubuntu kernel sources, the debian (and Ubuntu developer) way:

```
%sudo $SHELL
#cd /usr/src
#apt-get install wget
#wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-6.13.dsc
#wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-6.13.tar.gz
```

Ok, now that's make sure we have what we need to have, to build a kernel, and put everything into place:

```
#apt-get build-dep linux-image-generic build-essential dpkg-source
#dpkg-source -x linux-source-2.6.22_2.6.22-6.13.dsc
#ln -sf linux-source-2.6.22-2.6.22 linux
#cd linux
#cp /boot/config-2.6.20*generic .config
```

I have an X1300 and the Intel 3945, so I need to rebuild for my new kernel.  I'd better have the code before the machine's 'down and out!

First, the latest ATI binary driver:

```
#cd /usr/src
# mkdir ati; cd ati; wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.37.6-x86.x86_64.run
#bash *run --buildpkg Ubuntu/Feisty
#dpkg -i *.deb
```

Now, the IPW3945 driver (I'd like to switch to the later ipwifi, but that's far too much effort for this tutorial):
```
#cd /usr/src;mkdir ipw3945; cd ipw3945
# wget 'http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.1.tgz?download'
# tar zxvpf ipw3945-1.2.1.tgz
```

Ok, so we have our 'safety net'.  Let's build the kernel.  First, let's run through the new options.  It's generally safe to chose the defaults.  Usually.  Make sure you pay attention, though.  Turn off IRQBALANCE and any modules you won't need.  It'll make compile time faster.

```
#cd /usr/src/linux; make oldconfig
```

Now, this is going to take forever.  This was my SECOND build attempt (the first worked, but I forgot something, so I needed to start over.
```
#cd /usr/src/linux
#make-kpkg clean
#make-kpkg --append-to-version=-2-686-generic --initrd kernel_image kernel_headers
```

First, install the kernel headers.  If this fails, we won't be able to make new modules.
```
#cd /usr/src
#dpkg -i linux-headers-2.6.22-rc3-2-686-generic_2.6.22-6.13_i386.deb
```

All worked?  Ok, let's install the kernel.  Wait, we don't have support for the firmware, so let's copy that, first.  There's a better way, but this is fast and rogue.  ;)

```
#cp -R /lib/firmware/`uname -r` /lib/firmware/2.6.22-rc3-2-686-generic
```

Now, let's install the kernel:

```
#dpkg -i linux-image-2.6.22-rc3-2-686-generic_2.6.22-6.13_i386.deb
```

Ok, let's reboot into our new kernel.  When the system starts and askes 'Press Esc' for grub menu, press 'Esc', and choose the second option (2.6.22 Recovery Mode).

Let it boot, and when it prompts for the password, enter your password.

Let's make sure all partitions are mounted:
```
#mount -a
```

Ok, let's install fglrx:

```
#cd /usr/src; bzip2 -dc fglrx.tar.bz2 | tar xvpf - -C /usr/src/ati
#cd /usr/src/ati/modules/fglrx
#bash make.sh
#mkdir /lib/modules/`uname -r`/misc
#cp fglrx.ko /lib/modules/`uname -r`/misc
#depmod -ae
#modprobe fglrx
```

Check to see if it loaded:
```
#dmesg | tail -5
```

This is a bit strange how Ubuntu does this: Binaries are tagged by kernel revision for support modules too.  Er, OK.  Let's copy the ipw3945 daemon over to this kernel version; we don't need to recompile (Exchange 2.6.20-15-generic with your prior kernel version.  It's probably easiest to just type ipw3945d- then press tab.):

```
#cp /sbin/ipw3945d-2.6.20-15-generic /sbin/ipw3945d-`uname -r`
#cd /usr/src/ip3945/ipw3945-1.2.1
#make
#make install
```

Finally, test to see that the ipw3945 driver works:
```
#modprobe ipw3945
```

If you get an error about not finding /sbin/ipw3945d-kernelversion, you either typo'd, for forgot to copy the ipw3945 daemon, above.

Now, this is somewhat divergent from Ubuntu's basic kernel version, but it's trivial to 'fall back'.  If it doesn't work, or you really want to go back, you can press 'ESC' at boot time, choose an older kernel, then 
```
apt-get --purge remove linux-headers-2.6.22\* linux-image-2.6.22\*
```

if you installed the updated ATI driver, you can reinstall the elder version with:
```
apt-get --reinstall install xorg-driver-fglrx linux-restricted-modules-2.6.20-16-generic
```

I found this thread using google to try to find out how to compile a kernel to include both of these drivers. This works great except, it's a little out of date...are there any plans to update this in the future? I was able to get it to work by going to the links for each of the kernel packages and finding the current one and doing the same for the ati driver as well. Another correction is that when you do ```
bash *run --buildpkg Ubuntu/Feisty
``` you get an error saying the package doesn't exist. Running ```
bash *run --listpkg
``` will reveal which packages are supported and when you view that you see it should be ```
bash *run --buildpkg Ubuntu/feisty (or Ubuntu/gutsy
``` notice the removal of the capitalized F and G for feisty and gutsy...not a big difference but it only works uncapitalized.

---

### Post by neptho on 2007-11-23
> **kill4killin said:**
> I found this thread using google to try to find out how to compile a kernel to include both of these drivers. This works great except, it's a little out of date...are there any plans to update this in the future?

Not directly.  I've spent hours upon hours trying to find simple workarounds for Gutsy to work with my 6400 with ATI video, and finally given up - everything I have managed to do requires even MORE kernel playground and isn't all that easy to track between different systems, so I'm sitting on Feisty until it's no longer feasible.

If anybody would like to take this over, or update it, they have my blessing.

---

