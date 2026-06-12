---
title: "No ethernet"
date: 2010-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d_fiumano on 2010-08-21
I recently installed Ubuntu 10.04 
Lucid (GNOME 2.30.2)on my Vostro 1000 and I'm pulling my hair out trying to figure out why my wifi works and my ethernet does not. I've been to a whole bunch of forums and no one can tell me what my problem is. It WAS working during the initial install but when I powered my laptop down and turned it back on today, my wifi works fine, but my ethernet will not connect. I tried typing in the MAC address & something about pinging which I could not understand for the life of me. I tried the terminal as well, but no dice. Any help would be mucho apriciado!
Thanks.

---

### Post by jcolyn on 2010-08-21
In the terminal enter```
 ping google.com
```If you get ping returns close the terminal and open firefox and enter ```
about:config
``` in the address bar. In the filter bar enter ```
ipv6
```In the line below which reads ```
network.dns.disableIPV6
``` look to see if the value is true. If it is false double click the line to change the value to true.

Close firefox and restart..

If this does not work go to network settings. Click proxy and make sure connect to the internet directly is ticked.

---

### Post by d_fiumano on 2010-08-22
I followed every step to the letter, and still no connection. This is driving me crazy.

---

### Post by jcolyn on 2010-08-22
> **d_fiumano said:**
> I followed every step to the letter, and still no connection. This is driving me crazy.

Have you checked to see if onboard ethernet is enabled in the BIOS?

Have you had the cable checked to see if it is the correct (straight) cable. Crossovers won't work.. Have a computer shop check the cable..

---

### Post by d_fiumano on 2010-08-22
I know it's not the cable because it's the same cable I've always used. I also tried a cold reboot and it worked...but I had to warm reboot for a display problem and now I'm back to square one with wifi working fine, but no LAN. How do I enable the ethernet the BIOS?

---

### Post by jcolyn on 2010-08-22
> **d_fiumano said:**
> How do I enable the ethernet the BIOS?

Depending on models at startup hit either f2, f10, or delete to enter the bios setup. Look for ethernet and see if it is set to enable or disable.

I'm not familiar with your model so it may or may not have that option in the bios..

---

### Post by d_fiumano on 2010-08-23
Well, I checked the BIOS and it is enabled, but It still won't connect. My ethernet jack doesn't light up green either. This is veeeeery aggravating.

---

### Post by s0rc3r3r on 2010-08-23
At times when I get network issues I used to try and restart the networking protocols by issuing commands from the terminal

[http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-linux-network-service/](http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-linux-network-service/)

do check out that link.

---

### Post by d_fiumano on 2010-08-23
Great suggestion [s0rc3r3r]("http://ubuntuforums.org/member.php?u=1127668"), but still no go. My wifi is functioning beautifully, but no LAN connection. I tried terminal, I tried looking in the BIOS, and I tried google. No one an tell me what my problem is nor how to fix it. There has got to be ONE magic sudo command to fix this. I just want to be able to connect to auto eth1 like I used to in  9.14 Karmic. This is driving me up the walls...Should I switch back?

---

### Post by ptn107 on 2010-08-23
```
echo "r8169" | sudo tee -a /etc/modules
```

then restart

---

### Post by jcolyn on 2010-08-23
> **d_fiumano said:**
> My ethernet jack doesn't light up green either.

You should have both a green and yellow (amber) light. If neither are lit you could have a dead ethernet board.

At the terminal type ```
lspci
``` and copy the results here..

---

### Post by d_fiumano on 2010-08-23
Ok. Here's what I got:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

---

### Post by jcolyn on 2010-08-23
This is your wired ethernet card. You might try doing a google search to see if there are any issues with getting it configured.

```
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

This site shows your card to be compatible so I am inclined to believe your card could be bad but one more check should be done.

I don't recall where in gnome but I think in system look for hardware drivers. Click it and enter your password. Wait a few moments for the detection to take place to see if something like b44 shows up. If it is not activated click activate and wait for the driver to be downloaded and installed.

[http://www.fsf.org/resources/hw/net/wired-ethernet](http://www.fsf.org/resources/hw/net/wired-ethernet)

---

### Post by d_fiumano on 2010-08-23
Ok. I tried to look for the drivers, but it only shows the wireless driver. My ethernet card was working fine in 9.14 and when I first installed 10.04, but when I rebooted, it decided to let me know it hated me & not work anymore. I even tried Wicd and now the jack's leds don't light up anymore. I'm losing what's left of my mind (which, mind you, was an hor dourve to begin with)! I also tried a code in the terminal "lshw -C network" and I got this:
68.1.106 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:c0200000-c0203fff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1_rename
       version: 02
       serial: 00:1d:09:ba:14:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff

I want to get the part that says  *-network DISABLED to ENABLED.

**HOLD IT!!!**
I think I got it working!!

---

