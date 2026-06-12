---
title: "Wireless suddenly won't work in 8.10"
date: 2008-12-25
forum: General Help
---

### Post by enchance on 2008-12-25
I've looked all around the web for an answer to my wireless prob but still nothing, so I thought that now would be a good time to consult the forums. I have an Intel PRO/Wireless card which worked out of the box in 8.04, but after a fresh install of 8.10 my wireless doesn't work anymore. Apparently this is an issue for those trying to access WEP 64bit connections (which I have), but even after installing WICD the wireless still won't work!

After 2 weeks of trying to fix this thing, I'm still nowhere getting it to work. If I can't get my wireless to work by the end of the year I'm going to install 8.04 instead. Grrrrr...

This is what my lspci looks like:

```
    00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
    00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
    00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
    00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
    00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
    00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
    00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
    01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
    02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
    02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
    02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
    02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

This is what my lsusb looks like:

```
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I also took out my WEP but still no success. It can't even detect my wireless connection (WICD) when I'm already standing next to my router.

Anything else I can try? I'm open to anything at this point.

---

### Post by pastalavista on 2008-12-25
Can you access the internet via ethernet with the upgrade? What is the output of```
lshw -C network
``` Did the wireless work with the live CD? *(it doesn't have a physical switch you forgot to flip, does it?)*

---

### Post by enchance on 2008-12-25
> **pastalavista said:**
> Can you access the internet via ethernet with the upgrade? What is the output of```
lshw -C network
``` Did the wireless work with the live CD? *(it doesn't have a physical switch you forgot to flip, does it?)*

My wireless is always on, in fact, the led which signals the presence of a wireless connection is on right now...but no wireless connections are detected in WICD. Accessing the net through a wired connection is ok though.

I tried the LiveCD and it detects my wireless but I can't connect to it. I installed WICD since Mint 6 only has a drop-down selection for a 40/128bit Key and a 128bit Passphrase...no 64bit. :'(

I honestly don't think WICD is the problem here. Should I take it out and put back network-manager? If so, how do I do that?

Results of lshw -C network:

```
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:d8:10:51
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:51:0b:a2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:09:27:67:57:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Just to make it clear, my WEP sports a 64bit encryption. I know it's not safe but most of the places I go to have WEP 64bit security (like my school/Starbucks/gym) so if I can't even detect my WEP here at home then what more out there?

---

### Post by socrazy143 on 2008-12-25
What channel is your router set to.  I visited your site and it looks like you are in the US but there is a known problem for those outside the US using channels 12 and 13.  Here is a post with a workaround, might work for you, might not:

[http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8.10-upgrade-689834/](http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8.10-upgrade-689834/)

---

### Post by enchance on 2008-12-25
> **socrazy143 said:**
> ...there is a known problem for those outside the US using channels 12 and 13.

I'm outside the US and I'm using channel B/G 11.

---

### Post by enchance on 2008-12-30
*bump*

Help anyone?

---

