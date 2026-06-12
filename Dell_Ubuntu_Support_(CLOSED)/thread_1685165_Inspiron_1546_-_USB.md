---
title: "Inspiron 1546 - USB"
date: 2011-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by p0ptartz on 2011-02-10
EDIT: I installed Ubuntu 10.04 32-bit instead of 10.10. Everything worked perfectly. I do not need help anymore. 

I recently installed Ubuntu 10.10 64-bit and everything worked perfectly (wireless, networking, etc..) or so I thought. For some reason I can't figure out why the USB ports do not work. I'm trying to use my USB mouse and get some files off a USB stick. I have a Dell Inspiron 1546 (laptop) with 3 USB ports. 

I have searched this forum a bunch of times along with Google and can't figure out why they don't work. I have checked my BIOS setting and USB is enabled, and they are up to date. 

In the Terminal I tried typing *lsusb* but nothing happens.
Here's what it says when I type *lspci*
```
ryan@Ryan:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```Appreciate it if anyone could help me out. =]

---

### Post by se7ensamurai on 2011-02-24
Looks like i wasn't alone. I just bought an Inspiron 1546, quickly installed Kubuntu 10.10 32bit. A few days later installed Skype and the cam didn't work. lsusb brought back nothing. Cam and everything works beautifully under Win7. Scoured the interwebs for advice and drivers etc. I hadn't tried to use a usb drive on it until i found this post. Thumb drive didn't work either. Ran a fresh install of 10.04, and '**majikalllll**y!' USB works. awesome huh? 

must not be that common of an issue eh?

Thanks p0ptartz!

---

### Post by kikenovic on 2011-07-11
It seems it only happens on the Inspiron 1546, I'm on ver 11.04 64 bit and the issue is still there.

You got it to work with a 32 bit version, what happens if you want to go above 4 gb Ram ?

You think I could report this as a bug?

Thanks.

---

