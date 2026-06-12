---
title: "No wireless adapter detect ubuntu 9.04"
date: 2012-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SweetNandy on 2012-01-07
I installed ubuntu 9.04 version in my Dell System XPS L502X

i cannot connect to the wireless network but i can connect to the wired network.

i dont think my wireless card is detected ..

The output of lspci command is

00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4b (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: Intel Corporation Device 008a (rev 34)
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


I dont kow what the command is for since i am pretty much new to the linux environment.

please help me through dis..

---

### Post by mörgæs on 2012-01-07
Hi, welcome to the fora.

9.04 is obsolete. Better to install one of the supported releases:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by SweetNandy on 2012-01-07
thanks for enlightening....

This is very helpful.....

---

### Post by MARP1961 on 2012-01-07
I notice you have a Dell. Dells commonly have wifi cards produced by Broadcom. Ubuntu may not find this driver on install. You may need to install it whilst you are connected by ethernet cable. Read the following information and instructions carefully if you have problems:
[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

Firstly, you need a copy of a current version of Ubuntu to install:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by MARP1961 on 2012-01-07
**I'm so sorry**, I didn't read the other posts first before posting my answer (unforgivable). From the output details you posted it appears you **do not **have a Broadcom card. 

Perhaps just installing and updating to the latest version of Ubuntu will be enough to get it all working.

 [http://www.ubuntu.com/download/ubuntu/download  ]("http://www.ubuntu.com/download/ubuntu/download")

[]("http://www.ubuntu.com/download/ubuntu/download")

---

