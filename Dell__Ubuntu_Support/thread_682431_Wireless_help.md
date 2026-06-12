---
title: "Wireless help?"
date: 2008-01-30
forum: Dell  Ubuntu Support
---

### Post by rorshach on 2008-01-30
so i know my wireless card is (kind of) working, because i can view all my possible wireless connections, but then when i try to connect to one of them, im unsuccesful.  theres those two little grey dots, and im guessing theyre both supposed to turn green...well one of them does, but the other one never quite makes it.

if you cant tell im a pretty hardcore nub...please dont make me reinstall windows.  i just want the internet, please help me?

---

### Post by faulkes on 2008-01-30
> **rorshach said:**
> so i know my wireless card is (kind of) working, because i can view all my possible wireless connections, but then when i try to connect to one of them, im unsuccesful.  theres those two little grey dots, and im guessing theyre both supposed to turn green...well one of them does, but the other one never quite makes it.

if you cant tell im a pretty hardcore nub...please dont make me reinstall windows.  i just want the internet, please help me?

Which wireless card are you using (intel or broadcom on the dell)?

Are you using WEP/WPA on the network you are trying to access?

Can you post the output of a "/sbin/iwlist ethX scanning" command?
 - note replace ethX with the actual interface name (eth0, eth1, etc)

Faulkes

---

### Post by rorshach on 2008-01-30
> **faulkes said:**
> Which wireless card are you using (intel or broadcom on the dell)?

Are you using WEP/WPA on the network you are trying to access?

Can you post the output of a "/sbin/iwlist ethX scanning" command?
 - note replace ethX with the actual interface name (eth0, eth1, etc)

Faulkes

im using the broadcom.  im not really sure what "wep/wpa" means, but the network im trying to access is one of those massive downtown wireless networks (although, there are also private wireless networks in my building that i cant connect to either).  i know it works because im connected to it on another comp right now.

as far as the output, how do i know which interface to put?

i know im really clueless about this stuff, but im really eager to learn and i really appreciate the help

---

### Post by rorshach on 2008-01-30
the other thing that i was worried about, is that my computer keeps freezing for no real reason.  now granted i still havent gotten my ATI accelerated graphics driver, do you think thats the cause of the problem, or should is my comp just not powerful enough for gutsy?

---

### Post by faulkes on 2008-01-30
> **rorshach said:**
> im using the broadcom.  im not really sure what "wep/wpa" means, but the network im trying to access is one of those massive downtown wireless networks (although, there are also private wireless networks in my building that i cant connect to either).  i know it works because im connected to it on another comp right now.

as far as the output, how do i know which interface to put?

i know im really clueless about this stuff, but im really eager to learn and i really appreciate the help

Typically the interface will be eth1 (eth0 being the wired network card)

WEP/WPA is encryption used to protect the network, typically a key required to join it (in the most basic of sense).

The install of drivers for the broadcomm card, do you know if they are the restricted broadcom drivers or the windows based ndiswrapper (I would assume they are likely the restricted).

iirc you can probably tell by issuing a "/sbin/lsmod | grep bcm" and pasting the output back here.  Also helpful might be the output of a "/sbin/iwconfig eth1" command.

Faulkes

---

### Post by faulkes on 2008-01-30
> **rorshach said:**
> the other thing that i was worried about, is that my computer keeps freezing for no real reason.  now granted i still havent gotten my ATI accelerated graphics driver, do you think thats the cause of the problem, or should is my comp just not powerful enough for gutsy?

Well, one problem at a time :) can you describe what happens before the freeze occurs? i.e. are you actively doing something and it just freezes? or is the the machine going into a hibernate state? etc.. etc..

If it does freeze, does X restart if you issue a CTRL-ALT-BACKSPACE command sequence?

Would also be helpful if you posted some specs on your machine (model, ram, cpu, video card type, all that stuff)
Faulkes

---

### Post by jan quark on 2008-01-30
can you please post the results of the following terminal commands here ?

```
iwconfig
```
```
ifconfig
```
```
lspci
```
```
sudo iwlist scan
```
during the last one you will probably have to type in your login password

these codes will shed some light on your network status

---

### Post by rorshach on 2008-01-30
> **faulkes said:**
> Well, one problem at a time :) can you describe what happens before the freeze occurs? i.e. are you actively doing something and it just freezes? or is the the machine going into a hibernate state? etc.. etc..

If it does freeze, does X restart if you issue a CTRL-ALT-BACKSPACE command sequence?

Would also be helpful if you posted some specs on your machine (model, ram, cpu, video card type, all that stuff)
Faulkes

haha sorry, youre right one problem at a time.  its just frustrating because i keep trying to get the information for you nice folks...but halfway through the computer locks up and i have to turn it off and start it back up.

the freezing occurs very randomly.  usually when im just switching from one window to another.  ill just click to bring a window into the foreground and then all of a sudden the window is only semitransparent, and the computer wont do anything.  i tried the CTRL-ALT-BACKSPACE suggestion but it did nothing.

im not totally sure where i can find the specs to my machine (though if you tell me how, ill be more than happy to) but from what i know it s a dell latitude d6-10 with a 1.6 ghz processor and a half a gig of ram.

ill post the results of those commands momentarily, just as soon as the machine fires back up

---

### Post by rorshach on 2008-01-30
the freezing has gotten a lot worse, i literally cant run all of those commands and then copy and paste them into a document without the entire computer locking up before i finish...any ideas?

---

### Post by rorshach on 2008-01-30
turned off the dektop animations and now its running fine.  here are those command outputs

**_iwconfig_**

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"merr.com"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0B:85:72:68:DC   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**_if config_**

```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:14:F7:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:08:92:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:213 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20520 (20.0 KB)  TX bytes:22705 (22.1 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**_lspci_**


```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

**_sudo iwlist scan_**

l```
o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:49:F5:0C
                    ESSID:"dlcm17"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-50 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 196ms ago
          Cell 02 - Address: 00:1B:5B:F3:53:09
                    ESSID:"2WIRE088"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-70 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 324ms ago
          Cell 03 - Address: 00:12:17:7A:76:DA
                    ESSID:"rockys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-70 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 216ms ago
          Cell 04 - Address: 00:18:39:52:29:DB
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-73 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 212ms ago
          Cell 05 - Address: 00:18:39:73:9D:1B
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-80 dBm  Noise level=-72 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 448ms ago
          Cell 06 - Address: 00:0B:85:72:67:EF
                    ESSID:"madcitybroadband"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-80 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 440ms ago
          Cell 07 - Address: 00:0B:85:72:68:DC
                    ESSID:"merr.com"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=81/100  Signal level=-53 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 220ms ago
          Cell 08 - Address: 00:16:01:D6:C8:9E
                    ESSID:"Awesomezone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-67 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 2952ms ago
          Cell 09 - Address: 00:1B:FC:57:EE:92
                    ESSID:"bowling"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-73 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 12ms ago
          Cell 10 - Address: 00:0B:85:72:68:DD
                    ESSID:"msncity"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-50 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 224ms ago
          Cell 11 - Address: 00:30:65:28:13:BC
                    ESSID:"Basement Airport"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=67/100  Signal level=-72 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 304ms ago
          Cell 12 - Address: 00:0B:85:72:68:DF
                    ESSID:"madcitybroadband"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-50 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 224ms ago
          Cell 13 - Address: 00:0B:85:72:67:ED
                    ESSID:"msncity"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-77 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 440ms ago
          Cell 14 - Address: 00:0B:85:72:67:EC
                    ESSID:"merr.com"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=60/100  Signal level=-78 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 440ms ago
          Cell 15 - Address: 00:14:6C:7D:6C:D8
                    ESSID:"Apt 13 - 9"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-82 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 412ms ago
          Cell 16 - Address: 00:16:B6:C5:95:09
                    ESSID:"Apt 11"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-83 dBm  Noise level=-72 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 468ms ago
          Cell 17 - Address: 00:18:39:5A:95:7F
                    ESSID:"Brady for MVP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-82 dBm  Noise level=-72 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 824ms ago
          Cell 18 - Address: 00:1B:5B:24:F7:19
                    ESSID:"carlosnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=60/100  Signal level=-78 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 348ms ago
          Cell 19 - Address: 00:13:10:63:B9:52
                    ESSID:"wheatnoodle"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=53/100  Signal level=-85 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 612ms ago
```


once again, thanks for all the help guys.  i really appreciate it

---

### Post by faulkes on 2008-01-30
Well, from what I can see, the card is being picked up properly and is able to find / connect to various access points.

I don't see it getting an ip address (usually assigned via dhcp).

so, first, I would select the ESSID (wireless network) you want to connect with manually

iwconfig eth1 essid <wireless network name>
i.e. iwconfig eth1 essid madcitybroadband

then try to have the dhcp client get an address from the network using the below command

sudo /sbin/dhclient eth1

If you are assigned an address, then we can look at why it's not automatically doing this for you.

Faulkes

---

### Post by rorshach on 2008-01-30
heres what i got

iwconfig eth1 essid merr.com

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.


sudo /sbin/dhclient eth1

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:08:92:60
Sending on   LPF/eth1/00:14:a5:08:92:60
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

did i do everything right?

---

### Post by faulkes on 2008-01-30
> **rorshach said:**
> heres what i got

iwconfig eth1 essid merr.com

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.


Sorry

sudo iwconfig eth1 essid <wireless network name>

> 

sudo /sbin/dhclient eth1

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:08:92:60
Sending on   LPF/eth1/00:14:a5:08:92:60
Sending on   Socket/fallback
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

did i do everything right?

Aside from my mistake of not prefacing the sudo command on iwconfig, yes.  Not sure where else to look for answers right now so I'm going to give it some thought (although do retry the above with the sudo change).

Faulkes

---

### Post by rorshach on 2008-01-30
alright after typing it in the new way that you showed me, nothing happened (as far as i could tell)  then i reentered the other one that you gave me again and heres what i got this time

sudo /sbin/dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 6354
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:08:92:60
Sending on   LPF/eth1/00:14:a5:08:92:60
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by faulkes on 2008-01-30
Just for kicks, try

sudo iwconfig eth1 essid Awesomezone
sudo /sbin/dhclient eth1

See if it assigns you an address.  I'm just trying to determine if this is a card issue still or if there is something else required from the AP side of things we don't as of yet know about.

Faulkes

---

