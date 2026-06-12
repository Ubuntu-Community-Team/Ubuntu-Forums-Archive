---
title: "Xubuntu 14.04.2 LTS freezes randomly"
date: 2015-06-27
forum: Desktop Environments
---

### Post by priya6 on 2015-06-27
Hello! 
I have been using Xubuntu 14.04.2 LTS since Dec 2014, but off-late it has started freezing frequently and quite early into the session, and I am unable to perform any action, except switching off the power button and starting it again. 
I don't understand why this has started happening, and there seem to be no overheating issues. 
I'll be thankful for any help! 

Best

---

### Post by v3.xx on 2015-06-27
Sure your not just going to swap?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=slow+swap&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=slow+swap&sa=Search&cof=FORID:9)

What are your computer specs?

---

### Post by priya6 on 2015-09-15
> **v3.xx said:**
> Sure your not just going to swap?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=slow+swap&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=slow+swap&sa=Search&cof=FORID:9)

What are your computer specs?

The swappiness value is set at the default 60. 

Here is the result of lspci :

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
03:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)

If you need any other information please let me know! 
  -  Ctr+Alt+F1 also does not work.
  - I also realized that I can operate the keyboard and the mouse, and run programs as usual, except that the display has frozen completely and I cannot see what I am running. I can open new tabs on firefox etc. but I cannot see what I'm doing on the screen. 
  - The freezing happens randomly and the laptop definitely does not seem to have overheated. 
  - I also tried changing the Nvidia driver from Nouveau Open Source driver to the proprietary,tested NVIDIA binary driver - version 340.76, after going through [this]("http://askubuntu.com/questions/542841/ubuntu-14-04-display-freezes-occasionally"). However that did not work. I am yet to see if switching to a USB mouse will solve the problem.

(Will update soon.)

[EDIT]
I realized that the freezing happens only when I use the touchpad on the laptop. 
Thanks a lot!!

---

### Post by BidongGong on 2015-09-16
I get similar problem, any help will be appreciated.  Or I should just try debian before long ? 


@Bulbul:~/Downloads/app$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
@Bulbul:~/Downloads/app$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]
02:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

---

