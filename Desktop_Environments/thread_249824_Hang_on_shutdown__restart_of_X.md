---
title: "Hang on shutdown / restart of X"
date: 2006-09-03
forum: Desktop Environments
---

### Post by oled on 2006-09-03
When I shutdown my pc or restarts X (with ctrl+alt+backspace). 8 out of 10 times it hangs. No screen output just a blank screen! I have to kill it with the power button.

What log files should I be looking at in order to find my problem?

It's my HTPC so there is no monitor connected only a television. 

My hardware is an athlon 64 on a Ati rs480 chipset motherboard, with an onboard ati xpress 200 gfx. 

/Ole

---

### Post by tymek666 on 2006-09-03
I had exactly the same problem when i used MSI ati xpress 200 based board. I've tried ubuntu 5.04 and 5.10 and this problem still appeared. Now i'm switch to nf4 board.

---

### Post by locque on 2006-10-27
I am having the same problem with my setup... Are you able to switch to a console tty by hittin <CTRL><ALT><F3>? Mine hangs up when I do that also. I too have an AMD 64 and am running the 64-bit version of dapper with the fglrx driver. I wonder if it is not related to the video driver as I previously thought but if it is related to the kernel configuration???

I too would like to know which log files would generate any kind of help on this. Xorg.log and syslog show nothing that i've seen

---

### Post by wolphin on 2006-10-27
I have an ATi X700XL, running the i386 version of Edgy and exactly the same happens to me, but I get a flurry of colours across the screen instead of a blank one. This happens when I shutdown, restart, or switch runlevel..

If there's a solution, please let us know! Thanks.

---

### Post by xfi155 on 2007-12-12
ubuntu 7.10 fglrx x hangs

I also am having issue with hangs, 

Motherboard is an Asus M2A-VM HDMI (Hdmi disabled), Socket A2 64x2 running at 32 bit.  Currently using propritary ATI fglrx driver.  Ubuntu has been excellent.  Surprised this one got by.

Jim

jim@family-linux:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

---

### Post by soan on 2008-02-20
same problem here 

have a Asus M2A-VM HDMI mb

had to run dpkg-reconfigure -phigh xserver-xorg and revert back to the vesa driver

this is more than likely a problem the the ati driver :(

---

### Post by oled on 2008-02-20
I actualy bought a M2A-VM HDMI, but I'm not using the onboard gfx. Instead I'm using a geforce 8600 gts. It's working flawless.

/Oled

---

