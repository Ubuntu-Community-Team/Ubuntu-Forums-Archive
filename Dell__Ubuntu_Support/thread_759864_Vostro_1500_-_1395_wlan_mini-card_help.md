---
title: "Vostro 1500 - 1395 wlan mini-card help"
date: 2008-04-19
forum: Dell  Ubuntu Support
---

### Post by uknowho008 on 2008-04-19
hey, i got a new laptop yesterday and i was super excited about it until i realized my wireless doesnt work. ive been searching all night and some this morning and haven't been able to get it up and running yet. i tried ndiswrapper and when i tried to install both the r140747 and dells driver i get this

```

installing r140747.exe ...
couldn't find SourceDisksFiles section - continuing anyway...
couldn't get manufacturer section - installation may be incomplete

```

also when i run lspci i cant seem to find my wireless eithe. this is what i get.

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

so it looks like i need some help. thanks.

---

### Post by uknowho008 on 2008-04-19
ok, so i realized i needed to extract the inf and sys file so i did that and now it says the driver is installed. i also ran

```
sudo depmod -a
```

and 

```
sudo modprobe ndiswrapper
```

and im still not seeing any wireless but im making my way down the ubuntu wiki

---

### Post by AndrewTheArt on 2008-04-19
Try 

```
echo "ndiswrapper" >> /etc/modules
```

and restart your computer for all the changes you've made to take effect.

By the way, certain modules that come with the kernel/Ubuntu for your wireless device may need to be blacklisted. For example, I have a Atheros wireless card and I had to run - 

```
sudo -i
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
rmmod ath_pci
```

Look for "Add Windows Wireless Drivers" (or whatever it says) in the Ubuntu menu to see if you can remove modules previous installed. Finding a good guide for your particular wireless card is probably the route to go, though...

---

### Post by uknowho008 on 2008-04-19
ndiswrapper -l now gives me

```

bcmwl5 : driver installed
        device (14E4:4315) present

```

but i still have no wireless. what am i not doing?

---

### Post by uknowho008 on 2008-04-19
> **uknowho008 said:**
> ok, so i realized i needed to extract the inf and sys file so i did that and now it says the driver is installed. i also ran

```
sudo depmod -a
```

and 

```
sudo modprobe ndiswrapper
```

and im still not seeing any wireless but im making my way down the ubuntu wiki

just tried that. i get permission denied. even with sudo.

---

### Post by uknowho008 on 2008-04-19
thanks for the help. i finally just got it working with

```
sudo ndiswrapper -m
```

and then adding ndiswrapper to /etc/modules

awesome, thanks guys.

---

### Post by AndrewTheArt on 2008-04-19
If you feel so inclined, make a mini-guide explaining exactly where you downloaded the drivers, what steps you took, etc. That will greatly help out future users :KS

---

### Post by uknowho008 on 2008-04-19
> **AndrewTheArt said:**
> If you feel so inclined, make a mini-guide explaining exactly where you downloaded the drivers, what steps you took, etc. That will greatly help out future users :KS

should i make a new thread or use this one?

i really just used the ubuntu ndiswrapper wiki but got caught up on extracting the drivers (which were the dell drivers) and i had to add ndswrapper to /etc/modules and restart before it would work. i dont think id be very good at writing a guide but i will if you think i should.

---

### Post by SOULRiDER on 2008-04-20
I ahve a vostro 1500 and wireless worked out of the box for me on Hardy.

---

