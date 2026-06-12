---
title: "USB Ports Not Working"
date: 2009-01-07
forum: General Help
---

### Post by cometa2k7 on 2009-01-07
I have 64-bit Intrepid installed on my Acer Aspire 5920, but mt USB port don't work. If I boot with a USB stick present, the LED within the stick will flash, as though being accessed, but it will not show up, nor be accessed at any time after.

I'll post the outcomes of lsusb and lspci here:
> nathan@nathan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

> nathan@nathan-laptop:~$ lsusb


lsusb gives no output at all.

If there are any other diagnostics which you would like me to run I can.

---

### Post by cometa2k7 on 2009-01-12
Bump

---

### Post by cometa2k7 on 2009-01-15
I just checked the live CD, and my USB ports worked, so I don't know why they don't now.

I could do with getting this fixed - networking to my other computer just to access a simple USB drive is a little annoying.

---

### Post by kokkus on 2009-01-15
There are some ways to fix this.
But first, is this a new problem? The unmounted USBs has nothing to do with your PC since they work from the LIve CD. 
Please check if they work on any of the older kernels (update points) u have on your grub list.
If there are none older kernels, go to the package manager, search for MountManager. Install that package and put something in all your USB ports like ipods and stuff like that. It will be easier for the mountmanager to recognize the ports if something is there.
Now open the Mount Manager (system > admin > MountManager) and there you'll see a list of all your devices.
Go to Tools > USB Device Manager and there you'll see everything.
Now click tools > restoration system. If any kind of device doesn't work you can restore it from there. 
Now you go to the partition menu and click Mount.

---

### Post by cometa2k7 on 2009-01-16
Nothing shows up in Mount Manager other than my CD drive and my harddrive.

I don't know whether or not it worked before, as I didn't use the USB ports for quite a while.

I just checked with my other kernel, and they still don't work, nor does Mount Manager pick them up.

---

