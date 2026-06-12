---
title: "NVIDIA - two GTX 750 Ti cards on EVGA X58 motherboard cause Kernel Panic"
date: 2015-10-24
forum: Gaming &amp; Leisure
---

### Post by ralphScan on 2015-10-24
I have a 2009-vintage EVGA X58 motherboard with an Intel Core i7.

It works just find with one EVGA Geoforce GTX 750 Ti card, but I need to put a second card in this system.


PANIC: early exception 08rip 246.10 error ffffffff 8103df66 cr2 (plus some long address values)

Here's my hardware configuration with the one card:

  [INDENT]system.hardware.primary_video.vendor = 4318 (0x10de)
  system.hardware.primary_video.product = 4992 (0x1380)
  system.hardware.serial = 'OEM'
  system.hardware.uuid = '00000000-0000-0000-0807-060504030201'
  system.board.serial = ''
  system.firmware.vendor = 'Phoenix Technologies, LTD'
  system.firmware.version = '6.00 PG'
  system.firmware.release_date = '10/06/2009'
  system.hardware.vendor = 'OEM'
  system.hardware.product = 'OEM'
  system.hardware.version = 'OEM'
  system.chassis.manufacturer = 'OEM'
  system.board.product = '141-BL-E757'
  system.board.version = 'Tylersburg'
  system.board.vendor = ' EVGA'
......
42: PCI 200.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_1380
  Unique ID: B35A.UhMN+4kVS20
  Parent ID: 3hqH.h8i6gWf1Jl1
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x1380 
  SubVendor: pci 0x3842 "eVga.com. Corp."
  SubDevice: pci 0x3753 
  Revision: 0xa2
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf1000000-0xf1ffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (ro,non-prefetchable)
  Memory Range: 0xde000000-0xdfffffff (ro,non-prefetchable)
  I/O Ports: 0xbf00-0xbf7f (rw)
  Memory Range: 0xf2f00000-0xf2f7ffff (ro,non-prefetchable,disabled)
  IRQ: 44 (1626566 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00001380sv00003842sd00003753bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia is active
    Driver Activation Cmd: "modprobe nvidia"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)
 
 
kernel version is 3.2 - Ubuntu release is 12.04 - and I'll use these dual GPUs for computing and driving 6 monitors.

----- /proc/cmdline -----
  BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=2f47b7b4-b6c7-4b61-9b60-69b887bb03e7 ro recovery nomodeset
....
[/INDENT]
  
                

I realize I'm using a PCI Express 3.0 card in a PCI Express 2.0 motherboard, but I'm hoping to find out what's causing the kernel panics so I can replace it.

Any suggestions welcome.   I don't have Windows installed on this machine, so I need to use Linux tools to diagnose the problem.

---

### Post by oldfred on 2015-10-24
I am surprised even one Maxwell card works.

 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.

      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by ralphScan on 2015-10-24
I updated to 12.04.05 - but finding reliable information on the best-supported driver is hard to come by.

I fixed the two cards in one machine with the following BIOS tweak:

Go to the **Frequency/Voltage Control** setting - adjust the Memory Low Gap to the largest available value (3 in this case)

Thanks for the other links, I will check them out.

---

### Post by efflandt on 2015-10-28
GTX 750's work with older kernels, just not with default **nouveau** or initial **nvidia-current** 304 driver in 14.04 (although, strangely it worked with whatever nvidia-current 304 version is in 12.04). When I installed 14.04 I had to install **nvidia-331** (or **nvidia-331-updates**) from recovery boot with networking enabled before I could even get X to run. I am currently using a newer driver from graphics-drivers/ppa.```
efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

efflandt@XPS-8100-1404:~$ nvidia-smi
Wed Oct 28 17:52:32 2015       
+------------------------------------------------------+                       
| NVIDIA-SMI 352.55     Driver Version: 352.55         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 750 Ti  Off  | 0000:01:00.0      On |                  N/A |
| 32%   26C    P8     0W /  38W |    134MiB /  2047MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      1417    G   /usr/bin/X                                     113MiB |
|    0      2210    G   compiz                                          11MiB |
+-----------------------------------------------------------------------------+
```

---

### Post by oldrocker99 on 2015-10-29
I don't believe that the 750ti has a socket for SLI, which may be your problem. Do you have a SLI connector between the two cards? If not, that's your problem.

---

