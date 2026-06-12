---
title: "System hangs with compiz sometimes"
date: 2009-08-02
forum: Desktop Environments
---

### Post by alamuru420123 on 2009-08-02
Hi all,

I've got a peculiar problem and it's rather difficult to pin down the cause for it. My system hangs randomly when resizing windows, alt-tabbing through them, or sometimes even when a window pops up. When this happens, my screen freezes up. Usually the mouse still works, but sometimes even that gets stuck. Nothing else works, not even ctrl+alt+F1. The only way out is a hard reboot. 

Has anyone experienced something similar?

One sure fire way to get it to hang is by using the J2EE edition of Eclipse 3.5 (Galileo) and try to open Preferences. It works if I completely disable compiz, but it hangs everytime I open it with compiz running. 

I've got compiz-fusion running with the highest option selected in the appearances window. It works normally without any lag or anything. Also, I've got AWN running along with the entire MacOS theme as per this tutorial:

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

Also, this is on my Acer 4530 laptop with GeForce 9100MG graphics chipset.

I really would like not to have to disable compiz since I love my customised desktop a little too much. Also, I wouldn't be able to use AWN then.

Any help will be appreciated.

---

### Post by alamuru420123 on 2009-08-03
bump!

---

### Post by marjeo on 2010-11-30
I also experience that once in a while. I'm using hp mini 1001TU. Please... Any help from the experts please...

---

### Post by alamuru420123 on 2010-11-30
Sorry for not replying. I got this fixed by manually updating to a newer version of NVidia drivers directly from nvidia.com.

Hope that helps.

---

### Post by sherghan on 2011-02-28
Same problem here.
System sometimes hangs without any possibility to revive other there hardware reset.
Right now turning all desktop effects and restarting X-es helped, yet it's a temporary solution.


:?: @alamuru420123: What version of nVidia drivers have helped?



Ubuntu 10.10 Maverick
> root@mma:/# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
root@mma:/# lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 041e:4080 Creative Technology, Ltd 
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@mma:/# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               1197.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
root@mma:/# uname -a
Linux mma 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
root@mma:/# dpkg -l 'nvidia-current*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================
ii  nvidia-current               260.19.06-0ubuntu1           NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases    260.19.06-0ubuntu1           Modaliases for the NVIDIA binary X.Org driver


---

### Post by alamuru420123 on 2011-02-28
@Sherghan: I had this problem about 2 years ago. After an upgrade to 10.10 completely trashed my system, I performed a fresh 10.10 install and I don't have this problem anymore.

What I did back then was to just download the latest drivers for my card directly from nvidia and install that instead of ubuntu's built in one. Don't remember which version it was though.

I would suggest you try the same, the driver ubuntu provides is not always the latest.

Edit: Now that I think about it, when I did the fresh install a few days ago, I didn't even bother getting the nvidia driver from ubuntu. Directly downloaded it from nvidia's site and installed it and it works fine. Mind you, the problem is that every time something updates the kernel, X will crash and you will need to reinstall nvidia drivers again. Not a biggie, but just so you know.

---

### Post by sherghan on 2011-03-01
@Alamuru420123: Thanks for your fast replay.

I should correct: running the system on standard nVidia driver(260.19.06) without any desktop effects didn't help either - after about 6h my system hanged as it was earlier.
... Also running the newest drivers(260.19.36) didn't help.

Right now I'm trying to live with it using the nouveau (open source driver for nVidia).
...Seems stable, yet there are no desktop effects nor 3D acceleration(in general).

I hope that later on the switch to 11.04 will solve the problem.

P.S.
I know that Hardware is fully functional - it runs Win7 without a problem. :cry:

---

### Post by alamuru420123 on 2011-03-01
I don't doubt your hardware :), I'm sure it works fine. One last thing you can try is downgrade your driver to an older version (259 or 258 perhaps?) and see if it works fine. nvidia sometimes comes out with buggy releases which get patched in some future version. And if it doesn't work, perhaps a downgrade might? I had this issue several years ago on an nvidia system on Windows, so perhaps it's worth a shot.

---

