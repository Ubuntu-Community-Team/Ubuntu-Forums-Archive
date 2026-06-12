---
title: "problem with adsl modem lan port"
date: 2010-11-21
forum: Desktop Environments
---

### Post by H.A.M.I.D on 2010-11-21
hi everyone
 
today i installed ubuntu 10.10 (for the first time) . my modem was working fine with lan cable . then i used additional driver to install my vga card (ati 5770) driver . after download and installing driver , ubuntu asked me to restart so the driver can be activated . after i restarted my pc the lan led of adsl modem turned off and ubuntu couldent find the modem . even in windows 7 i tried to connect the modem but the lan led did not turn on ! really confiused !
 
 
any comment ? 
 
 
thank you very much.

---

### Post by azkraja on 2010-11-23
It seems the problem in modem, check power supply of modem, otherwise it should work for one of the OS.

---

### Post by H.A.M.I.D on 2010-11-23
thanks for your answer.
 
modem works with usb cable but doesnt work with lan . i executed " lspci " command in terminal and got this :
 
 
> 00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.3 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:03.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)
05:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
05:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

---

