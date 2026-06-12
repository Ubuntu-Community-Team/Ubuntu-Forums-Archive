---
title: "dota 2 crashing in-game ubuntu 14.04"
date: 2014-08-19
forum: Gaming &amp; Leisure
---

### Post by gdholly on 2014-08-19
Hi guys,

I play dota 2 on native linux and it is crashing multiple times per game.  The game I just played crashed 5 times.  I'm not sure where to look for the crash logs, or any logs for that matter.

I run Ubuntu 14.04 with 16GiB of DDR3 RAM

Here is my graphics card (lspci -vnn | grep vga):
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R9 270] [1002:6811] (prog-if 00 [VGA controller])

Here is my CPU (/proc/cpuinfo)
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 60
model name      : Intel(R) Pentium(R) CPU G3220 @ 3.00GHz
stepping        : 3
microcode       : 0x9
cpu MHz         : 3000.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts $
bogomips        : 5998.25
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual

This is one half of a duo core processor

I have checked my firewall logs and it is not a network issue.  I have no dropped sessions.

What I am hoping to learn is where the dota 2 logs are so I can look at the crash messages, and how I can improve or fix this problem.

---

### Post by oldrocker99 on 2014-08-20
Which graphics driver are you using? The ATI fglrx driver may be the problem, or the open-source radeon driver may be the problem. Whichever one you have, try the other one and see if it makes a difference.

---

### Post by gdholly on 2014-08-20
I am using the X.org open source drivers right now.

Here is the message I am getting in syslog each time I crash:

kernel: [82420.026848] dota_linux[17041]: segfault at 0 ip b75e21d0 sp bf8f5168 error 4 in libc-2.19.so[b74b4000+1a9000]

---

### Post by oldrocker99 on 2014-08-21
You may need to install the ATI fglrx drivers, which are available this way:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update 
sudo apt-get install fglrx-installer-13
sudo shutdown -r now
```

This will enable the PPA, which has the latest Ubuntu-ready ATI and nVidia drivers, update your sources, install the fglrx driver, and reboot.

Once you've done that, post the results of:
```
glxinfo
```

---

### Post by bizhat on 2014-08-23
xorg-edgers do not support fglrx on Ubuntu 14.04 (they have very outdated fglrx, that is released even before R9 270 ?)

For you card, you need AMD Cayalyst beta installed. Open source driver don't have good support for R9 270. Or you need a kernal upgrade + latest open source driver.

Post result of

```

glxinfo | grep OpenGL

```

---

### Post by belarrius on 2014-08-25
I have play Dota 2 with Catalyst 14.2 on ATI HD 5830 and i have no problems. But with Catalyst 14.4 the game crash after  ~5-10min of game.

I have Ubuntu 14.04 64bit with Kernel 3.13.0-35 with HD 5830 for this test.

---

### Post by bizhat on 2014-08-26
> **belarrius said:**
> I have play Dota 2 with Catalyst 14.2 on ATI HD 5830 and i have no problems. But with Catalyst 14.4 the game crash after  ~5-10min of game.

I have Ubuntu 14.04 64bit with Kernel 3.13.0-35 with HD 5830 for this test.

HD 5000 have better support in both Catalyst and Open source driver. But R9 270 won't work properly with default open source driver provided with Ubuntu 14.04, you may need to use Catalyst or get newer open source driver/kernel. If you still have HD 5830, post a benchmark result here

[http://ubuntuforums.org/showthread.php?t=2131425](http://ubuntuforums.org/showthread.php?t=2131425)

---

### Post by belarrius on 2014-08-26
> **bizhat said:**
> HD 5000 have better support in both Catalyst and Open source driver. But R9 270 won't work properly with default open source driver provided with Ubuntu 14.04, you may need to use Catalyst or get newer open source driver/kernel. If you still have HD 5830, post a benchmark result here

[http://ubuntuforums.org/showthread.php?t=2131425](http://ubuntuforums.org/showthread.php?t=2131425)

Awww... It's bad :( i'm sorry

---

### Post by gdholly on 2014-08-27
Here's my glxinfo | grep OpenGL:

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:

---

### Post by belarrius on 2014-08-28
VMware? You play with VMware??  Dota2 Exist on Steam Linux

---

### Post by maxinstuff2 on 2014-09-15
You definitely need the latest beta drivers from amd's website.

I will post a guide on how to get r9200 series cards to work properly with *buntu 14.04 when I get a few minutes because I just went through it and it's fiddly at the moment.
With the stock open source drivers you can't even get hardware acceleration right now on this card.

---

### Post by maxinstuff2 on 2014-09-17
Guide is up:
[http://ubuntuforums.org/showthread.php?t=2244651](http://ubuntuforums.org/showthread.php?t=2244651)

---

