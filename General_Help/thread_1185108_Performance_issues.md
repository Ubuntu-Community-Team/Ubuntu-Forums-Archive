---
title: "Performance issues"
date: 2009-06-11
forum: General Help
---

### Post by acole76 on 2009-06-11
I am new to Linux.

I am running Ubuntu 9.04 and I am experiencing very slow performance, basically, new windows are slow to paint. The processor constantly bounces between 10% and 40%.  My machine has 2 GB memory and ran Windows XP with no problem. The processes that seem to consume the most CPU are Xorg and firefox, which seems logical. One thing to point out is that I am running dual monitors and have a very high resolution (1280 x 1024).  The only applications I have installed, that weren't part of the base install, are Eclipse, JRE (of course), DbVisualizer and Jets3t.  Rendering new windows or clicking through tabs is painfully slow.

Any help is appreciated.

---

### Post by jken146 on 2009-06-11
Please post the specs of your system.  CPU, RAM and graphics card are the important ones.

Turning off 'Desktop Effects' in System > Preferences > Appearance should help for a start.  Also will turning off various services that you don't use (these might be Tracker, Bluetooth, ...) in System > Administration > Services.

---

### Post by colau on 2009-06-11
> **acole76 said:**
> I am new to Linux.

I am running Ubuntu 9.04 and I am experiencing very slow performance, basically, new windows are slow to paint. The processor constantly bounces between 10% and 40%.  My machine has 2 GB memory and ran Windows XP with no problem. The processes that seem to consume the most CPU are Xorg and firefox, which seems logical. One thing to point out is that I am running dual monitors and have a very high resolution (1280 x 1024).  The only applications I have installed, that weren't part of the base install, are Eclipse, JRE (of course), DbVisualizer and Jets3t.  Rendering new windows or clicking through tabs is painfully slow.

Any help is appreciated.
Disable desktop effect.
System>Preferences>Appearence>Visual Effects tab
Can you post
```

sudo fdisk -l
lspci
lshw

```

---

### Post by acole76 on 2009-06-11
Thank you for assisting me.  I overstated the memory, 1GB instead of 2.  I have attached the requested details.

CPU : Intel(R) Pentium(R) D CPU 2.80GHz
MEM : DIMM DDR Synchronous 533 MHz (1GB)
VID : ATI Technologies Inc RV370 [Radeon X300SE]

Visual effects are already turned off.  I disabled the bluetooth service.

---

### Post by lovinglinux on 2009-06-12
The Remote Desktop can cause high CPU usage and spikes. Disable it in the Startup Applications and reboot.

I also have a thread with a few [tips to improve performance](http://ubuntuforums.org/showthread.php?t=1152095). I have managed to double Firefox performance since Jaunty installation.

I presume you have the proprietary drivers for you graphics card installed.

---

### Post by acole76 on 2009-06-12
> **lovinglinux said:**
> I presume you have the proprietary drivers for you graphics card installed.

No, I did download them, but I figured the "certified" drivers would perform better.  I will try installing the drivers provided by the vendor.

```

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```I added this to /etc/X11/xorg.onf and I do notice a performance boost, but still not to an acceptable level.

---

### Post by acole76 on 2009-06-12
> **acole76 said:**
> I will try installing the drivers provided by the vendor.

Yeah right!

```

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

```

this error does seem to be well documented on this forum, I will spend some time pouring over the many posts.

---

