---
title: "Wireless internet"
date: 2009-02-10
forum: General Help
---

### Post by JLloyd on 2009-02-10
I know i just asked another question but..

one more thing.

I have wireless internet on this computer and i had to set it up with some trouble and time.

Will i have to re-establish a connection to the computer or what?

---

### Post by pytheas22 on 2009-02-10
I'm not sure what you mean.  Are you asking whether you would have to configure the wireless again if you reinstall Ubuntu?  In that case, yes.  Otherwise, please clarify your question.

I'm also happy to help you set the wireless up again if that's what you need...I know that wireless can be endlessly confusing if you're new to Linux, but once you deal with it enough times to understand what's going on, it's not that hard.

---

### Post by JLloyd on 2009-02-10
> **pytheas22 said:**
> I'm not sure what you mean.  Are you asking whether you would have to configure the wireless again if you reinstall Ubuntu?  In that case, yes.  Otherwise, please clarify your question.

I'm also happy to help you set the wireless up again if that's what you need...I know that wireless can be endlessly confusing if you're new to Linux, but once you deal with it enough times to understand what's going on, it's not that hard.

yes, i was wondering i have to configure it again. With windows all i had to do was take a USB device and transfer info to the computer with cable...

---

### Post by pytheas22 on 2009-02-10
Do you remember what you did to set it up the first time?  And what is the output of these commands:
```

lshw -C Network
lspci -nn
lsusb
uname -rm
```

With that information I can hopefully provide you with a succinct list of steps to get the Internet working on a new installation.  Unfortunately it probably has to be a little more complicated than simply copying a .exe file from another machine, but it shouldn't be too hard.

---

### Post by JLloyd on 2009-02-10
> **pytheas22 said:**
> Do you remember what you did to set it up the first time?  And what is the output of these commands:
```

lshw -C Network
lspci -nn
lsusb
uname -rm
```

With that information I can hopefully provide you with a succinct list of steps to get the Internet working on a new installation.  Unfortunately it probably has to be a little more complicated than simply copying a .exe file from another machine, but it shouldn't be too hard.

where do i input these commands? does not work in CMD :S
srry i am fairly nub

---

### Post by JLloyd on 2009-02-10
bump pytheas22

---

### Post by pytheas22 on 2009-02-10
> where do i input these commands? does not work in CMD :S
srry i am fairly nub

You can open a terminal by going to Applications>Accessories>Terminal.

---

### Post by JLloyd on 2009-02-11
After: lshw -C Network 

*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:b6:36:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:c2:20:f8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:67:f5:7c:a5:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


After: lspci -nn

0:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
05:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]


After: lsusb

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


After: uname -rm

2.6.27-7-generic i686

---

### Post by JLloyd on 2009-02-11
bump pytheas22 or anyone who can comprehend the code output

---

### Post by JLloyd on 2009-02-11
bump

---

### Post by pytheas22 on 2009-02-11
Thanks for the information.  Your wireless card uses the 'b43' driver.  On a new installation, the following steps should be sufficient to get the wireless working:

1. download [this file]("http://burnthesorbonne.com/files/b43_firmware.tar.gz") on a computer with Internet access and transfer it to your Ubuntu machine.  Save it on the desktop there.

2. run these commands in Ubuntu:
```

cd ~/Desktop
tar -xzvf b43_firmware.tar.gz
sudo cp -R b43/ /lib/firmware/
sudo cp -R b43legacy/ /lib/firmware/
```

Then reboot and your wireless should work.
> 
bump pytheas22 or anyone who can comprehend the code output 

Just for future reference: please don't bump threads unless no one has responded for more than a couple days.  I always try to answer as fast as I can, but please remember that everyone on this site is a volunteer and most of us have real jobs that prevent us from responding immediately :)

---

### Post by JLloyd on 2009-02-11
ok no problem, thanks for the warning

---

### Post by JLloyd on 2009-02-11
working perfectly now. Thank you very much

---

### Post by pytheas22 on 2009-02-11
Glad it's fixed :)

---

