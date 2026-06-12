---
title: "[SOLVED] Help with desktop effects please"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by slughappy1 on 2008-01-31
I just installed Gutsy and when I went to System -> Preferences -> Appearance and tried to turn on the desktop effects I get and error "Desktop effects could not be enabled". Can anyone tell me why not?

---

### Post by edm1 on 2008-01-31
What graphics card does your computer have? If you dont know can you post the output of typing 'lspci' in the terminal?

---

### Post by slughappy1 on 2008-01-31
I think Intel Integrated Graphics Media Accelerator 3100 Inspiron 1420, but just incase

```
jason@Bighead:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by edm1 on 2008-01-31
As far as i know the Intel GM965/GL960 card is blacklisted and doesnt work however i may be wrong. If it does work you will need to search the forums for a howto on how to install the drivers for your specific graphics card.

---

### Post by Therion on 2008-01-31
Someone on the Compiz' forums has your same integrated graphics chipset and they seem to have had some success getting Compiz to work.  

See the relevant thread [HERE]("http://forum.compiz-fusion.org/showthread.php?t=6738").

Good luck!

---

### Post by slughappy1 on 2008-01-31
why would it be black listed?

---

### Post by edm1 on 2008-01-31
> **slughappy1 said:**
> why would it be black listed?

Intel has not released linux drivers for your card so it cannot support 3D acceleration. You will have to wait for Intel to release the drivers or for them to be reversed engineered but that is unlikely to happen soon as graphics cards are very complex things. [This could be good news for the near future.]("http://linux.slashdot.org/article.pl?sid=08/01/31/1415251&from=rss")

---

### Post by slughappy1 on 2008-01-31
But see, I thought that my laptop (and all devices on it) would be fully supported because it is a Dell that comes with Ubuntu pre-installed on it. Why would it not have 3d? That just seems weird to me

---

### Post by edm1 on 2008-01-31
> **slughappy1 said:**
> But see, I thought that my laptop (and all devices on it) would be fully supported because it is a Dell that comes with Ubuntu pre-installed on it. Why would it not have 3d? That just seems weird to me

The dell ubuntu laptops only come with Intel X3100 or nVidia 8400 GS. If you really did by one with ubuntu preinstalled then to my disbelief they've giving you the wrong laptop because as far as i can tell yours definately hasn't got one of those cards! Unless anyone else can shed light on this i say ring them and shout at them!

---

### Post by slughappy1 on 2008-01-31
well I bought a dell and it came with ubuntu so...

---

