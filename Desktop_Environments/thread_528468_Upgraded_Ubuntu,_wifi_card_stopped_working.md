---
title: "Upgraded Ubuntu, wifi card stopped working"
date: 2007-08-17
forum: Desktop Environments
---

### Post by eeefresh on 2007-08-17
I have an old Sony Vaio laptop with a Netopia wifi card. I have been dual-booting XP and Ubuntu 6.10 for a while now, and the wireless card worked flawlessly right out of the box on both OS's. However, I recently updated the Ubuntu partition to 7.04, and for some reason the wifi card no longer works. I can't connect to the Internet at all.

I know its not the card or my network setup, because it still works fine when I boot into XP. Also, I am sure my card works with Ubuntu, since it worked fine in version 6.10.  But as a last-ditch effort, I reinstalled 6.10 again, and it still doesn't work!

 I am positive that there is a setting somewhere that got screwed up when I upgraded, but I know nothing about Ubuntu network settings. When I go into connection properties, it says 

**Connection**
Name: lo (no other options available in the drop down)
Status: Idle

I also went into* System --> Networking Tools* and selected the "Unknown Interface (ra0)" device, it seems to be transmitting bytes at a constant rate.  but lo  and eth0 are not.

I must confess I am a networking noob, and it took me days to even get it set up right in XP!

Can anyone provide some advice?

---

### Post by angryfirelord on 2007-08-18
Did you check the NetworkManager applet and see if that was picking up any connections?

---

### Post by eeefresh on 2007-08-18
Where can I find that?

---

### Post by angryfirelord on 2007-08-18
It's in the upper right corner, next to the clock. Feisty has it pre-installed, but Edgy does not.

---

### Post by eeefresh on 2007-08-18
It just says

Connection
Name: lo (no other options available in the drop down)
Status: Idle

---

### Post by ugm6hr on 2007-08-18
I believe the Realtek drivers need to be installed manually in Feisty, and Network Manager needs to be uninstalled.

```
lspci -nn | grep Ethernet
lspci -nn | grep Network
```
One of those will tell you what hardware you have.

```
lshw -C network
```
Will tell you what driver Fesity is using.

You'll have to do a search here, or in the wiki to see how to install this.

---

### Post by eeefresh on 2007-08-18
I'll try that, but I am not sure what it will tell me.  Remember, I reinstalled Edgy, so Feisty still isn't on the machine.

This is all very frustrating.  Why would it work, without any configuration, for several months, then suddenly stop working with an upgrade?  And ywhy would it not work any longer when I downgrade to what I had previously?

---

### Post by eeefresh on 2007-08-18
Okay, when I tried entering 
[PHP]lspci -nn | grep Ethernet[/PHP]
 or
[PHP] lspci -nn | grep Network[/PHP]
in terminal, it gave me nothing.  But when I entered
[PHP]lspci -nn[/PHP]
it gave me this:
[PHP]00:00.0 0600: 8086:3575 (rev 02)
00:01.0 0604: 8086:3576 (rev 02)
00:1d.0 0c03: 8086:2482 (rev 01)
00:1d.1 0c03: 8086:2484 (rev 01)
00:1d.2 0c03: 8086:2487 (rev 01)
00:1e.0 0604: 8086:2448 (rev 41)
00:1f.0 0601: 8086:248c (rev 01)
00:1f.1 0101: 8086:248a (rev 01)
00:1f.3 0c05: 8086:2483 (rev 01)
00:1f.5 0401: 8086:2485 (rev 01)
00:1f.6 0703: 8086:2486 (rev 01)
01:00.0 0300: 1002:4c59
02:02.0 0c00: 104c:8021 (rev 02)
02:05.0 0607: 1180:0476 (rev 80)
02:05.1 0607: 1180:0476 (rev 80)
02:08.0 0200: 8086:1031 (rev 41)
07:00.0 0280: 1814:0201 (rev 01)[/PHP]
When I ran 
[PHP]lshw -C network [/PHP]
it gave me this:
[PHP]WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 08:00:46:43:92:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 multicast=yes
       resources: iomemory:d0204000-d0204fff ioport:4000-403f irq:9
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@07:00.0
       logical name: ra0
       version: 01
       serial: 00:d0:41:a0:82:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:36000000-36001fff irq:9

[/PHP]

---

### Post by ugm6hr on 2007-08-18
I don't know whay it didn't work with a frsh Edgy install - I have never used Edgy.

I believe this might help:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Or else this:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Sorry I can't help any further.

---

### Post by eeefresh on 2007-08-19
I installed Dapper Drake last night...still wouldn't work.  However, it still works in Windows...

---

### Post by UbuntuniX on 2007-08-27
Try the instructions here:
```
http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu#Feisty_Fawn_.287.04.29
```

Worked for me, although it's extremely slow as of right now.

---

### Post by eeefresh on 2007-08-29
Okay, I finally had some time to monkey with this some more.  Here's an update.

I did another fresh install of 7.04 and updated everything via a wired connection.  The netowrk manager in the upper right of my screen is showing my SSID, so it must be detecting the network.  However, the little signal bar beside it shows that its not getting a signal.  So....it looks like it sees it, but it doesn't see it?  Maybe I just need to reconfigure the settings under network settings?  Physical distance isn't an issue because I have it set up about two feet from the router.

lspci says...

[PHP]
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
07:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

[/PHP]

iwconfig says...

[PHP]lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP]

and if config says...

[PHP]eth0      Link encap:Ethernet  HWaddr 08:00:46:43:92:5E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe43:925e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2579189 (2.4 MiB)  TX bytes:314008 (306.6 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

ra0       Link encap:Ethernet  HWaddr 00:D0:41:A0:82:AC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:878800 (858.2 KiB)
          Interrupt:9 
[/PHP]

---

### Post by eeefresh on 2007-08-29
Also, under network settings, roaming mode is enabled.  Is it supposed to be?

---

### Post by eeefresh on 2007-08-30
*cough cough*...bump....*cough cough*

---

