---
title: "L702x  how to shutdown GT555M"
date: 2011-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by n_u on 2011-12-29
Hi, 

Im new to linux and wanted to ask a few question about ubunutu on my Dell XPS17 l702x. 
In my xps17 i've switchable-grahpics (2730qm intel igp-nvidia gt555m). 
When i use ubunutu on my xps17 i've only 2.5 hours of battery when its fully loaded (to comparise with windows thats about 8-9 hours). 
I tried a lot of things to fix this problem, but since im quite new to linux im to failish to fix this.

At first I've tried Bumblebee, to fix the optimus problem. But it didnt work well. After that i tried Ironhide, it worked well (i could switch the GT555m off) but when i started a movie ubuntu crashed. It was faaaar from stable.
Now i'm back at the start and with Bumbleblee. I've created a cardon and cardoff file (i also did install acpi), the cardon and cardoff file have the following credentials: 

*(sudo touch cardon)   *
  \_SB.PCI0.PEG0.PEGP._PS0

*(sudo touch cardoff) *
\_SB.PCI0.PEG0.PEGP._DSM  {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0}  0x100 0x1A {0x1,0x0,0x0,0x3} \_SB.PCI0.PEG0.PEGP._PS3 


Becouse i cant get optimus working (probaly i did something wrong), i want to ask the following: 

- What am i doing wrong with the switchable-graphics. 

- Is it possible to disable the GT555m, i wont need it in ubunutu anyway since there are no proper games that will require a GT555m.


Thanks in advance.


*excuse for my bad englisch.

---

### Post by freyberry on 2012-01-17
**I finally figured out how to get the same battery life as on Windows (~7-8 hours with 9-cell battery).**

**If you want the full battery life, you need to install the 2.6 kernel.**

**Here's what you need to do (on x64):**

a) Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/)

b) download those three files:
   - linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb
   - linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb	
   - linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

c) open a terminal, cd into your download directory and execute this command:

sudo dpkg -i linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

a) download this: [https://lists.launchpad.net/hybrid-graphics-linux/sh3hFub0KkvH.sh](https://lists.launchpad.net/hybrid-graphics-linux/sh3hFub0KkvH.sh)

b) go into a terminal, cd into download directory and execute these commands:

  git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
  cd acpi_call
  make
  sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
  sudo depmod
  sh3hFub0KkvH.sh off

**The last command disables the NVidia card (more info here: [https://lists.launchpad.net/hybrid-graphics-linux/msg00663.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00663.html)). ****Note that you can still use Bumblebee**, if you want to play games for example.

---

### Post by sparhawkthesecond on 2012-05-12
Hi freyberry, I know this thread is a few months old, but did you find that disabling the Nvidia GPU also reduced the CPU heat and lowered the fan noise?

Cheers.

---

