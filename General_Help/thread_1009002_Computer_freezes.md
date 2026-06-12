---
title: "Computer freezes"
date: 2008-12-12
forum: General Help
---

### Post by oakTree26 on 2008-12-12
Im running 8.10 (upgraded) and for the last two weeks or so my computer regularly freezes up after some time. It always seems to happen when I run Firefox (3.0.4), but I don't know if there is a causal connection, as I have an open instance of Firefox running almost all the time.  I noticed however that when I use Opera my computer doesn't freeze. 

Having to restart the computer several times a day is a nuisance and I hope someone could shed light onto my condition.

Thanks!

Here are the specifications of my computer:
Release 8.10 (intrepid)
Kernel 2.6.27-9
Gnome 2.24.1
Memory 3.0 GB
Processor: AMD Athlon 64 X2 DualCore Processor 5200+

---

### Post by rakris on 2008-12-12
I dont think its because of firefox.

Run a memtest and check first...

---

### Post by Peter09 on 2008-12-12
I believe that Firefox is the culprit here, not sure what you can do for a fix until a new release comes out, (except use opera or another browser)

---

### Post by rakris on 2008-12-12
I dont understand.. why does it have to be firefox?

Why not bad RAM sectors and computer freezes coincidentally when using firefox? 

Just a hunch. You may be right:)

---

### Post by oakTree26 on 2008-12-12
How would I find out if something with my RAM is wrong? Also, when I boot into Windows, the computer never crashes. So, maybe not a hardware problem after all?

---

### Post by Peter09 on 2008-12-12
Well, if it freezes when using firefox, but not anything else then its associated with firefox. In general, Opera for instance, will use exactly the same resources on your computer as firefox. So its all pretty much common stuff.

It might not be firefox, but the is the obvious culprit.

---

### Post by wpshooter on 2008-12-12
See if you can uninstall Firefox 3 and reinstall and older version.  This will probably give you a pretty good idea if Firefox is the problem.  My guess is that it is.

---

### Post by iponeverything on 2008-12-12
post this -- might be a driver issue:

sudo lshw -short

---

### Post by oakTree26 on 2008-12-13
H/W path             Device       Class       Description
=========================================================
                                  system      GA-MA78GM-S2H
/0                                bus         GA-MA78GM-S2H
/0/0                              memory      128KiB BIOS
/0/4                              processor   AMD Athlon(tm) 64 X2 Dual Core Pro
/0/4/a                            memory      128KiB L1 cache
/0/4/c                            memory      512KiB L2 cache
/0/b                              memory      128KiB L1 cache
/0/d                              memory      L2 cache
/0/29                             memory      4GiB System Memory
/0/29/0                           memory      2GiB DIMM 800 MHz (1.2 ns)
/0/29/1                           memory      2GiB DIMM 800 MHz (1.2 ns)
/0/29/2                           memory      DIMM 800 MHz (1.2 ns) [empty]
/0/29/3                           memory      DIMM 800 MHz (1.2 ns) [empty]
/0/1                              processor   
/0/1/0                            memory      128KiB L1 cache
/0/1/1                            memory      512KiB L2 cache
/0/100                            bridge      RS780 Host Bridge
/0/100/1                          bridge      RS780 PCI to PCI bridge (int gfx)
/0/100/1/5                        display     Radeon HD 3200 Graphics
/0/100/1/5.1                      multimedia  RS780 Azalia controller
/0/100/a                          bridge      RS780 PCI to PCI bridge (PCIE port
/0/100/a/0           eth0         network     RTL8111/8168B PCI Express Gigabit 
/0/100/11            scsi0        storage     SB700/SB800 SATA Controller [IDE m
/0/100/11/0.0.0      /dev/sda     disk        500GB ST3500320AS
/0/100/11/0.0.0/1    /dev/sda1    volume      50GiB Windows NTFS volume
/0/100/11/0.0.0/2    /dev/sda2    volume      414GiB Extended partition
/0/100/11/0.0.0/2/5  /dev/sda5    volume      122GiB Linux filesystem partition
/0/100/11/0.0.0/2/6  /dev/sda6    volume      8887MiB Linux swap / Solaris parti
/0/100/11/0.0.0/2/7  /dev/sda7    volume      18GiB W95 FAT32 partition
/0/100/11/0.0.0/2/8  /dev/sda8    volume      265GiB Linux filesystem partition
/0/100/12                         bus         SB700/SB800 USB OHCI0 Controller
/0/100/12.1                       bus         SB700 USB OHCI1 Controller
/0/100/12.2                       bus         SB700/SB800 USB EHCI Controller
/0/100/13                         bus         SB700/SB800 USB OHCI0 Controller
/0/100/13.1                       bus         SB700 USB OHCI1 Controller
/0/100/13.2                       bus         SB700/SB800 USB EHCI Controller
/0/100/14                         bus         SBx00 SMBus Controller
/0/100/14.1          scsi4        storage     SB700/SB800 IDE Controller
/0/100/14.1/0.0.0    /dev/cdrom1  disk        DVD RW AD-7200A
/0/100/14.2                       multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                       bridge      SB700/SB800 LPC host controller
/0/100/14.4                       bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/e                     bus         TSB43AB23 IEEE-1394a-2000 Controll
/0/100/14.5                       bus         SB700/SB800 USB OHCI2 Controller
/0/101                            bridge      K8 [Athlon64/Opteron] HyperTranspo
/0/102                            bridge      K8 [Athlon64/Opteron] Address Map
/0/103                            bridge      K8 [Athlon64/Opteron] DRAM Control
/0/104                            bridge      K8 [Athlon64/Opteron] Miscellaneou
/0/2                 scsi7        storage     
/0/2/0.0.0           /dev/sdb     disk        4043MB SCSI Disk
/0/2/0.0.0/1         /dev/sdb1    volume      3855MiB Windows FAT volume
/0/3                 scsi6        storage     
/0/3/0.0.0           /dev/sdc     disk        320GB 0A
/0/3/0.0.0/1         /dev/sdc1    volume      298GiB Windows FAT volume
/1                   pan0         network     Ethernet interface

---

### Post by oakTree26 on 2008-12-16
My computer keeps on crashing. Since it happens when the single application I run is Firefox, there seems to be a connection. 

Anyone out there who can help? 

Is the only solution to downgrade to previous versions of Ubuntu and Firefox? 

(it happened while I was typing this message - feels most annoying...)

---

