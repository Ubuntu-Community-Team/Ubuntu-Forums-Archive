---
title: "PRO/Wireless 5300 AGN Stopped Working Abruptly"
date: 2009-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DrBubba on 2009-09-02
I installed 64-bit Jaunty on my Latitude E6500.  Everything worked out of the box except that yesterday for no apparent reason my wireless card stopped working.  It worked fine in the morning, then after transporting the machine around, suspending a couple of times and connecting to a couple of different LANs, wireless networking was disabled when it came back from being suspended.   Networking still works - my ethernet connection still works fine - just the wireless stopped.  Thinking that I'd inadvertently turned off wireless I tried re-enabling it via the NetworkManager applet only to find that the "Enable Wireless" checkbox is grayed out - though enabling networking isn't.  Booting into the live CD doesn't change anything - enabling wireless is still grayed out - when I got the machine that worked just fine.  As far as I can tell, nothing has changed in the software, it appears to be a hardware problem.  What else can I do to troubleshoot this and rule out a configuration or other issue - though I haven't touched anything - I just want to rule it out.  Running lspci -nn produces the following:
victor@bubba:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA RAID Controller [8086:282a] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 160M [10de:06eb] (rev a1)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]

and running lshw -C Network produces:

victor@bubba:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:a7:a5:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.7-7 ip=128.118.78.205 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:4a:96:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:b3:5e:76:60:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I wondered if somehow the driver module had become unloaded so I checked:

victor@bubba:~$ lsmod | grep iwlagn
iwlagn                114820  0 
iwlcore               106496  1 iwlagn
mac80211              251528  2 iwlagn,iwlcore
cfg80211               43680  3 iwlagn,iwlcore,mac80211

I figured that wasn't likely as I'd been getting the same result with the live CD but I had to check.  Any suggestions.  I'm a long time linux user (mostly Debian, but I've been using Ubuntu on my desktop machines for a few iterations now).

---

### Post by colinireland on 2009-09-02
Hey,

I am just after fixing the exact same problem you have. I have gone through hell and back and by fluke have just got it working 5min after reading you post. OK long story short...

This is what worked for me, right click the network manager >> Edit connections >> wireless tab. Now in my case there were two records of my home wireless network stored there. one was labelled as "never", the other "8 min ago" (from my external card) so i deleted the one marked never and bingo, everything was working normally!!!

I really hope this helps. I have gone through this problem three times already. Booting from the live CD didn't help, A fresh installation didn't help. I ended up going as far as installing vista and then reinstalling ubuntu. That fixed the problem temporarily.  I hope this fixes it for good but I doubt it somehow.

I have a Dell 1545 using bcm4312 drivers. ifconfig and lspci show that the card is recognised and hardware drivers show that the broadcom sta driver is activated!


Colin

---

### Post by DrBubba on 2009-09-03
Thanks.  Unfortunately that didn't work for me.  I don't have multiple entries for any wireless networks.  I do have multiple entries for my office LAN - which I've just cleaned up - all to no avail I'm afraid.  Restarting network manager hasn't helped either.

---

### Post by colinireland on 2009-09-04
Same thing is after happening again. Have you had any luck fixing your card?

---

### Post by colinireland on 2009-09-05
I followed a post saying to edit /etc/NetworkManager/nm-system-settings.conf

change:

[ifupdown]
managed=false

to this:
[ifupdown]
managed=true

worked for me

---

### Post by jward3010 on 2009-10-04
Something similar kind of worked to a degree for me. I got the card to discover wireless networks with "iwlist" by setting the "wlan0" to "up".
```
sudo ifconfig wlan0 up
```
Then
```
sudo iwlist wlan0 scan
```
And networks appeared!

Although network manager still thought it was disabled and I couldn't see any networks through nm, so connecting was still going to be through iwconfig which is complicated and annoying if you don't know how.

---

### Post by jward3010 on 2009-10-04
> **colinireland said:**
> I followed a post saying to edit /etc/NetworkManager/nm-system-settings.conf

change:

[ifupdown]
managed=false

to this:
[ifupdown]
managed=true

worked for me
I'll give this a go when I reinstall network-manager, currently on wicd and it works without problems.

---

### Post by guru.gv on 2010-05-25
> **jward3010 said:**
> Something similar kind of worked to a degree for me. I got the card to discover wireless networks with "iwlist" by setting the "wlan0" to "up".
```
sudo ifconfig wlan0 up
```Then
```
sudo iwlist wlan0 scan
```And networks appeared!

Although network manager still thought it was disabled and I couldn't see any networks through nm, so connecting was still going to be through iwconfig which is complicated and annoying if you don't know how.

This worked for me ! Dell Studio with Intel 5300 wlan card. on ubuntu 10.04

---

