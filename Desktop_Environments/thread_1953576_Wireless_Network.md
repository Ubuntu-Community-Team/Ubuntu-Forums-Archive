---
title: "Wireless Network"
date: 2012-04-06
forum: Desktop Environments
---

### Post by smss on 2012-04-06
Hi.
I using from Ubuntu 11.04 i686 and i can not see any wireless network! and when i create ad-hoc wireless network, i can not see that by another computers! ( another computer have a Ubuntu 9.10 i386 ).
How can i create or see or connect to wireless networks?
Thanks for answering to my question.
All the best.

---

### Post by bogan on 2012-04-07
Hi!, **smss**,

Do you have a Network Manager Icon in the top Panel/Toolbar?; [ it is a Fan/Shell symbolizing a radio wave ].
If you have, a Right-Click on it should show both 'Enable Network' and 'Enable Wireless' Ticked, a Left-Click should show your network name if it is recognized.

What wireless network Adapter do you have?  & what driver ?

If you have a Windows/Ubuntu dual boot, does WiFi connect in Windows correctly?

Please post detail from Windows Device Manager>Network Adapter, or the output from Sudo lspci & sudo lsusb.

[  Paste them into a New Reply box, highlight them and press the '#' icon in the tool bar at the top, to enclose them in Code markers.]

If there is no particular reason to use an 'Ad-Hoc' mode, change it to 'Infrastructure' in 'Edit Connections', and check that it is set to connect automatically.

Chao!, **bogan**.

---

### Post by smss on 2012-04-08
Hi.
Yes, i have that icon and Wireless & Enable Network are enable.
And i have Windows7 and does not have any problem for create the ad-hoc network! and play with wireless network on windows without any problem.
My Wireless adapter is D-Link DWA-525 ( N 150 ).
Another problem this is i can not see the Wireless networks from this Ubuntu but from windows, see many wireless network with different signal power.
My Devices info is : 
```

smss@smss-network:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:19.0 Ethernet controller: Intel Corporation 82567LM-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
06:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
07:02.0 Network controller: Ralink corp. Device 3060
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
smss@smss-network:~$ 


```
and 
```

smss@smss-network:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 09da:0260 A4 Tech Co., Ltd 
Bus 002 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
smss@smss-network:~$ 

```
Thank you.
*smss*

---

### Post by bogan on 2012-04-08
Hi!, **smss**,

Does your Network Icon have a vertical black line through it?  or does it have a sequence of arcs running through it, indicating it is scanning?

Do you get any windows showing 'Network disconnected', or similar?
 
Your Dlink DWA-525 (N150) uses the Ralink Corporation 3060 Chipset and the correct driver for that is probably rt3562sta.
My guess is you either have the wrong driver or two drivers conflicting with each other.

Have you checked out Dash>Additional Drivers, to see if it offers any thing.

 If you want to pursue this yourself here are two Links you could check out:
[http://ubuntuforums.org/showthread.php?t=1602218](http://ubuntuforums.org/showthread.php?t=1602218). 
It is a bit old but the content is helpful.

[http://ubuntuforums.org/showthread.php?t=1799715&highlight=network+Ralink+3060&page=2](http://ubuntuforums.org/showthread.php?t=1799715&highlight=network+Ralink+3060&page=2)
Especially Chill1555's Post #10, the file he refers to is the downloaded Ralink driver file from their website.

Please Post:```
sudo  lsmod | grep -e rt2 -e rt3
``` ```
cat /etc/modprobe.d/blacklist.conf
``` ```
sudo nm-tool
```
Chao!, **bogan**.

---

### Post by smss on 2012-04-09
Hi bogan, Thanks you for answering to my problem.
i think i have not the vertical black line and to ensure from this black line, i attached a screen shot from my Desktop. i think this is not scanning any thing!
If i not change the IP settings to Shared to Another Computer, i can not connect to Connection and faced with Network Disconnected.
also on Additional Drivers i not see any thing for wireless!
Output of Commands is:
```
 smss@smss-network:~$ sudo  lsmod | grep -e rt2 -e rt3
[sudo] password for smss: 
rt2800pci              18487  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
smss@smss-network:~$ 
``````
 smss@smss-network:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
smss@smss-network:~$ 

``````
smss@smss-network:~$ sudo nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:1C:C0:F3:B1:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0  [Wireless connection 1] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           no
  HW Address:        1C:7E:E5:5B:FD:86

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SMSS:            Ad-Hoc, 00:00:00:00:00:00, Freq 2412 MHz, Rate 0 Mb/s, Strength 0 WPA

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



smss@smss-network:~$ 

```
Thank you.
*smss*

---

### Post by bogan on 2012-04-09
Hi!, **smss**,

I do not see any screenshot, but no matter.

I am puzzled that nm-tool shows wlan0 as connected; Does a left-click on the Network icon not show any network name under the Wireless Network entry??

Please Post: ```
 sudo lspci -nnk | grep network
``````
 sudo lshw -C network
``````
 sudo iwconfig
``` ```
sudo iwlist scan
``` ```
 sudo rfkill list all
```It looks as though you will certainly have to blacklist the rt2xxo... drivers and download the correct one from Ralink/Downloads.

I need to do some research as it appears there is some disparity in the drivers recommended; either the RT3562STA or RT2862STA.

It is not clear to me how much tech knowledge of Linux you have. How do you feel about installing the Ralink driver as outlined in the two Links I Posted??

**Edit:** We also need to know what computer is involved and is it a wubi or a direct installation of 11.04.

Chao!, **bogan**.

---

### Post by bogan on 2012-04-09
Hi!, **smss**,

An Afterthought, rather clutching at straws:  It is a long time since I used 11.04, and no longer have it installed--:

In System Settings>Hardware do you have an app named 'Network'?

 If so, run it and select 'wireless', there may be an on/off button, which must be set to 'ON'. [At least that is how it is in 11.10.]

Chao!, **bogan**.

---

### Post by smss on 2012-04-10
Hi Bogan.
Excuse me for screenshot! i forgotten this! screen shot link is : [http://ubuntuone.com/1MKDRy505mCX2lBsHWqCMr](http://ubuntuone.com/1MKDRy505mCX2lBsHWqCMr)
When i click on the network icon in the top panel, i just see my wireless network! and does not see another!
```
smss@smss-network:~$  sudo lspci -nnk | grep network
[sudo] password for smss: 
smss@smss-network:~$ 
```
```
smss@smss-network:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:1c:c0:f3:b1:5c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.8-5 ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:d3200000-d321ffff memory:d3222000-d3222fff ioport:30e0(size=32)
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 2
       bus info: pci@0000:07:02.0
       logical name: wlan0
       version: 00
       serial: 1c:7e:e5:5b:fd:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-13-generic firmware=0.11 ip=10.42.43.1 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:d3000000-d300ffff
smss@smss-network:~$ 

```
```
smss@smss-network:~$  sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SMSS"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 32:21:5A:18:C6:7A   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
smss@smss-network:~$ 

```
```
smss@smss-network:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 32:21:5A:18:C6:7A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"SMSS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 405470ms ago
                    IE: Unknown: 0004534D5353
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100

smss@smss-network:~$ 

```
```
smss@smss-network:~$ sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
smss@smss-network:~$ 


```
i think this problem is arises from MAC address! but when i create or edit the Wireless networks, i not see any thing for MAC Address, But from Fedora , When i create i wireless network, i see MAC Address and i can see the another wireless networks from fedora, or i can see the my wireless network ( configured on fedora) by another computers.

---

### Post by bogan on 2012-04-10
Hi!, **smss.**

This has got bewildering a bit beyond my level of expertize, I am going to ask someone more knowledgeable to have a look. It probably needs some analysis of log files and I do not know a lot about what to look for.

To clarify things a bit, my understanding is that you have the network Manager Icon - though I cannot see anything I recognize as one in your screenshot - and it does show your network by name, but that if you double-click on that network entry nothing happens and you cannot make any connection, neither to your network nor to the Internet: or have I got that wrong??

I have received your email - an interesting suggestion but I do not feel like going that route as there is not much other info I could get that would be meaningful to me. As far as I can see from what you have Posted everything indicates networking is working - which it is not.

The only query I have at this moment is the failure  to get any output from: 
```
sudo lspci -nnk | grep network
```Would you try instead:
```
sudo lspci -nnk | grep -e net -e Net -e Ralink
```Though I do not expect it to give anything we have not already obtained.

Edit: It is also necessary to know which computer you are using and if Wubi or direct install.
Chao!, **bogan.**

---

### Post by chili555 on 2012-04-10
I think we have a level of confusion here. Your wireless seems to be working well. You have apparently set up an ad-hoc; that is, computer-to-computer network. The IP address you have:> Wireless Access Points 
    SMSS:            Ad-Hoc, 00:00:00:00:00:00, Freq 2412 MHz, Rate 0 Mb/s, Strength 0 WPA

  IPv4 Settings:
    Address:         [COLOR="Red"]10.42.43.**1**[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0
...indicates that *you* will be the access point of your local network and you are waiting for other computers to connect to *you*. Is that what you intended? Or did you intend to connect to a router or other access point and connect to the internet?

We need to understand your intention before we proceed.

---

### Post by smss on 2012-04-11
Hi everybody and special hi to the bogan.
My target of create a wireless network, this is to can i share the wired DSL by wireless.
I have a wired connection ( Internet ), and because another computers distance to router is very high and do not possible to connect as wired network to Internet, i want to create this wireless network, and connect to that by another computers.
I can create the wireless network, and see that, and that notification about connected to wireless network, but i can not connect to that by another computers.
i feel my Ubuntu does not know this PCI Card. i tested Ubuntu 10.04 for to see this problem, but i do not see any thing about wireless PCI card in 10.04 version!
if i disconnect wired network, my network icon this is: link -> [http://ubuntuone.com/2VWbpQTlIINOzi4fKhO7RZ](http://ubuntuone.com/2VWbpQTlIINOzi4fKhO7RZ)
can this problem from crash Ubuntu or any thing as this?
```

smss@smss-network:~$ sudo lspci -nnk | grep network
[sudo] password for smss: 
smss@smss-network:~$ 

``````

smss@smss-network:~$ sudo lspci -nnk | grep -e net -e Net -e Ralink
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-2 Gigabit Network Connection [8086:10cc]
07:02.0 Network controller [0280]: Ralink corp. Device [1814:3060]
smss@smss-network:~$ 

```and bogan: how can i help you to get up from bewildering?
Thanks.

---

### Post by smss on 2012-04-11
> **chili555 said:**
> I think we have a level of confusion here. Your wireless seems to be working well. You have apparently set up an ad-hoc; that is, computer-to-computer network. The IP address you have:...indicates that *you* will be the access point of your local network and you are waiting for other computers to connect to *you*. Is that what you intended? Or did you intend to connect to a router or other access point and connect to the internet?

We need to understand your intention before we proceed.
Hello
 I expect when i set up a wireless network that is visible to other computers and to be identified.
Thanks.

---

### Post by bogan on 2012-04-11
Hi!, **smss,**

You Posted: > ...and bogan: how can i help you to get up from bewildering?
Thanks. My bewilderment comes mostly from my self-expectation that after a long life mostly spent as a TroubleShooter - I am near to 88 - I should be able to understand the problem, even if unable to find a complete answer - see my signature.

In this case I have not really understood what the problem is right from the start, and, as Chili555 rightly pointed out, that should be the first step, not, as I did, to assume it would become clear when enough data had been obtained.

Your original Post said:>  i can not see any wireless network! and when i create ad-hoc wireless  network, i can not see that by another computers! ( another computer  have a Ubuntu 9.10 i386 ).  How can i create or see or connect to wireless networks?Your latest Posts say:>  I can create the wireless network, and see that, and that notification  about connected to wireless network, but i can not connect to that by  another computers.
and:
 I expect when i set up a wireless network that is visible to other computers and to be identified. I realize there is a language difficulty but it would help if you could explain in more detail both what you wish to achieve and in what way the present set-up fails to achieve it, in part or completely.

Is it your intention that all the computers can connect to the network and from there to the Internet, or is it to have a Home network that allows any computer to access & control any other and sync their data, but the Internet access is secondary or limited to the Host computer? -- or is it something else altogether??

Chao!, **bogan**.

---

### Post by chili555 on 2012-04-11
> I expect when i set up a wireless network that is visible to other computers and to be identified.On the other computers, when you put the cards in ad-hoc mode like this:```
sudo iwconfig wlan0 mode Ad-Hoc
```...then do they see this network? Do they not see it in Network Manager? Can they see it when they scan?```
sudo iwlist wlan0 scan
```

---

### Post by smss on 2012-04-12
Hi. and special hi to bogan & chili555.
Excuse me Bogan!!
My mean of "i can not see any wireless network" this is i can not see any wireless network except my created wireless network! and i want to all other computers can connect to me, and from me, connect to internet, and by this connection i can control and access to all of the computers and share some files.
------
and output of that commands on another computer is : 
```

ubuntu@ubuntu:~$ sudo iwconfig wlan0 mode Ad-Hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
ubuntu@ubuntu:~$ 

```and this command, despite wireless network on this computer, is : 
```

ubuntu@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:FB:33:4B:C6
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"sajad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005248eb18c4
                    Extra: Last beacon: 752ms ago
                    IE: Unknown: 000573616A6164
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706314420010D10
          Cell 02 - Address: D8:5D:4C:D4:6A:2D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_D46A2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019116521bc
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 000E54502D4C494E4B5F443436413244
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 00:1F:FB:26:30:3C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"26303C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000099220ea7c5
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 0006323633303343
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706314420010D1E
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500001E127A
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: 00:23:F8:D7:DA:91
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"mjk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e322e1ba
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 00036D6A6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

ubuntu@ubuntu:~$ 

```So i can not see my wireless network from another computers!!!!
Thanks.
*** all the best ***
***** smss *****

---

### Post by smss on 2012-04-15
Where is the problem?

---

### Post by smss on 2012-04-23
Hi.
I change the wireless hardware to older version and now this is working.
Thanks.
*** All the best ***

---

### Post by tumutanzi.com on 2012-05-19
It is really complicated if done by command.
I just using GUI method. It could not be easier.

---

### Post by smss on 2012-05-19
Your mean is Ubuntu can reconnoitre that device?
I like to know this route.

---

