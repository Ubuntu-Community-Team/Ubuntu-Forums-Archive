---
title: "xubuntu + firefox crashes at GNU.org"
date: 2011-01-09
forum: Desktop Environments
---

### Post by sumpkanin on 2011-01-09
I think this case is pretty funny, as I have been using xubuntu for a  couple of months - without a single crash or freeze. The first time it  freezes is when im looking through the GNU.org art gallery -  [http://www.gnu.org/graphics/graphics.html](http://www.gnu.org/graphics/graphics.html) -  see link to the exact page in the next post.

Not only firefox froze.. the whole xfce environment + mouse + keyboard  froze; with no other way out than making a hard reboot and starting  firefox in safe-mode and tjecking off the tab with the gnu gallery art. 

The graphics on the screen was messed up when it crashed the second time

I'm wondering how firefox would be able to make the whole desktop environment and keyboard input freeze..
---
I have run the page, 'GNU o Lantern' again, which causes the freeze - see next post.
The reason why I have posted this under Desktop Environments is that Firefox causes my Desktop Environment to freeze.

---

### Post by sumpkanin on 2011-01-09
! WARNING - do not follow the link if you don't want to risk your computer freezing up

I found out which link was the problem;
  'GNU o Lantern' at 'http://www.gnu.org/graphics/gnuolantern.html'

Ctrl+Alt+Backspace doesn't work to get the computer restarting, but I got it done with the 'Raising Elephants Is So Utterly Boring'

It seems the computer freezes when it is almost done loading the graphics. As i have succesfully run a mem-test on the system and it has 1gb ram at it's disposal, I can't imagine that could be the problem..

H/W path             Device      Class       Description
========================================================
                                 system      YYpire 5050
/0                               bus         Prespa M
/0/0                             memory      107KiB BIOS
/0/4                             processor   AMD Turion(tm) 64 Mobile Technology
/0/4/5                           memory      512KiB L2 cache
/0/1b                            memory      1GiB System Memory
/0/1b/0                          memory      1GiB DIMM DDR2 Synchronous
/0/1b/1                          memory      DIMM DDR2 [empty]
/0/100                           bridge      RS480 Host Bridge
/0/100/1                         bridge      RS480 PCI Bridge
/0/100/1/5                       display     RS482 [Radeon Xpress 200M]
/0/100/4                         bridge      RS480 PCI Bridge
/0/100/4/0           wlan0       network     AR5001 Wireless Network Adapter
/0/100/5                         bridge      RS480 PCI Bridge
/0/100/6                         bridge      RS480 PCI Bridge
/0/100/7                         bridge      RS480 PCI Bridge
/0/100/12            scsi2       storage     IXP SB400 Serial ATA Controller
/0/100/12/0.0.0      /dev/sda    disk        160GB WDC WD1600BEVS-2
/0/100/12/0.0.0/1    /dev/sda1   volume      9992MiB Windows NTFS volume
/0/100/12/0.0.0/2    /dev/sda2   volume      112GiB Windows NTFS volume
/0/100/12/0.0.0/3    /dev/sda3   volume      26GiB Extended partition
/0/100/12/0.0.0/3/5  /dev/sda5   volume      25GiB Linux filesystem partition
/0/100/12/0.0.0/3/6  /dev/sda6   volume      953MiB Linux swap / Solaris partiti
/0/100/13                        bus         IXP SB400 USB Host Controller
/0/100/13.1                      bus         IXP SB400 USB Host Controller
/0/100/13.2                      bus         IXP SB400 USB2 Host Controller
/0/100/14                        bus         IXP SB400 SMBus Controller
/0/100/14.1          scsi0       storage     IXP SB400 IDE Controller
/0/100/14.1/0.0.0    /dev/cdrom  disk        DVDRAM GSA-T20N
/0/100/14.2                      multimedia  IXP SB4x0 High Definition Audio Con
/0/100/14.3                      bridge      IXP SB400 PCI-ISA Bridge
/0/100/14.4                      bridge      IXP SB400 PCI-PCI Bridge
/0/100/14.4/1                    bridge      CB-712/4 Cardbus Controller
/0/100/14.4/1.1                  memory      FLASH memory
/0/100/14.4/1.2                  generic     ENE PCI Secure Digital Card Reader 
/0/100/14.4/1.3                  memory      FLASH memory
/0/100/14.4/1.4                  memory      FLASH memory
/0/100/14.4/2        eth0        network     RTL-8139/8139C/8139C+
/0/101                           bridge      K8 [Athlon64/Opteron] HyperTranspor
/0/102                           bridge      K8 [Athlon64/Opteron] Address Map
/0/103                           bridge      K8 [Athlon64/Opteron] DRAM Controll
/0/104                           bridge      K8 [Athlon64/Opteron] Miscellaneous
/1                   vboxnet0    network     Ethernet interface

---

### Post by sumpkanin on 2011-01-09
I might have found the solution myself.. Seems the graphics that needs loading on the page exceeds the assigned 64Mb ram in my BIOS, for the graphics card, xpress 200m - which uses 'shared memory architecture'. Would be a solution to set the assigned graphics ram to 128Mb, which I might consider - there have been other problems with playing some longer flash-streams on sites. In those situations I suddenly got a grey screen in place of the flash-stream; though no freezing.

---

