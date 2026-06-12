---
title: "The infamous Broadcom BCM4322 wireless card"
date: 2009-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nstein on 2009-09-10
Hello guys,

I've been searching for the past 3-4 days for a solution to me wireless problems. I've tried countless tricks with the b43 driver (which now I know does not support this card), ndiswrapper, compiled the new Broadcom driver myself, and nothing. My comp won't connect to my network. Even if I remove the security nothing happens.

Here is the result of various commands:
====
francois@francois-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:fa:43:e6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:26:8a:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:09:ee:36:b0:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
====
francois@francois-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
====
francois@francois-laptop:~$ iwlist eth1 scan
eth1      Interface doesn't support scanning.

====
francois@francois-laptop:~$ tail -n 50 /var/log/syslog | grep eth1
Sep 10 22:11:45 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Sep 10 22:11:45 francois-laptop avahi-daemon[2864]: Registering new address record for fe80::226:5eff:fe26:8a01 on eth1.*.
Sep 10 22:11:50 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Sep 10 22:11:54 francois-laptop kernel: [49811.812045] eth1: no IPv6 routers present
Sep 10 22:11:59 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Sep 10 22:12:09 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Sep 10 22:12:22 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Sep 10 22:12:43 francois-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 10 22:12:46 francois-laptop avahi-autoipd(eth1)[16369]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Sep 10 22:12:46 francois-laptop avahi-autoipd(eth1)[16369]: Successfully called chroot().
Sep 10 22:12:46 francois-laptop avahi-autoipd(eth1)[16369]: Successfully dropped root privileges.
Sep 10 22:12:46 francois-laptop avahi-autoipd(eth1)[16369]: Starting with address 169.254.3.130
Sep 10 22:12:50 francois-laptop avahi-autoipd(eth1)[16369]: Callout BIND, address 169.254.3.130 on interface eth1
Sep 10 22:12:50 francois-laptop avahi-daemon[2864]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.130.
Sep 10 22:12:50 francois-laptop avahi-daemon[2864]: New relevant interface eth1.IPv4 for mDNS.
Sep 10 22:12:50 francois-laptop avahi-daemon[2864]: Registering new address record for 169.254.3.130 on eth1.IPv4.
Sep 10 22:12:54 francois-laptop avahi-autoipd(eth1)[16369]: Successfully claimed IP address 169.254.3.130
====

I noticed that there is no dhcp offers received... This is very odd because I'm sure my router is working fine.

Any ideas ?

---

### Post by nstein on 2009-09-11
The model of my laptop is Dell XPS Studio 13 BTW

---

### Post by nstein on 2009-09-11
No one has any ideas on this ?

---

### Post by DodgeV83 on 2009-09-11
> **nstein said:**
> No one has any ideas on this ?

I have the Dell M1330.  Wireless was unusable for me until I switched to WICD instead of the gnome network manager.

By unusable I mean I would get drops every few minutes, and internet freezes.

sudo apt-get install wicd

Solved all my problems...

Well, all my problems besides trying to connect to a WEP secured router, you have to convert the passphrase password to HEX then change the password type to HEX to get that to work (WPA or unencrypted works fine)

[http://www.corecoding.com/utilities/wep2hex.php](http://www.corecoding.com/utilities/wep2hex.php)

If you don't have internet (duh cause you can't connect to the router) and need to convert to hex, run this in terminal

echo -n 'THEPASSWORDHERE' | od -An -t x1 | tr -d ' '

Oh yea, and after going into suspend mode, I can't pick up a new wireless connection.  I run this in the terminal to fix that:

sudo rmmod wl
sudo modprobe wl

Replace wl with whatever module corresponds to your wireless.  I forgot how to find that value, sorry.

---

### Post by community nerd on 2009-09-11
Are you sure you have that specific card?

---

### Post by nstein on 2009-09-12
> **community nerd said:**
> Are you sure you have that specific card?

Yes you can see it in the info I gave above.

---

### Post by jml on 2009-09-12
nstein, I feel your pain.  I have experienced nothing but frustration with any computer with a Broadcom chip set.  Having said that, I do have one suggestion.  Download a copy of gOS version 3.1.  Here is the distrowatch entry for it:

[http://distrowatch.com/table.php?distribution=gos](http://distrowatch.com/table.php?distribution=gos)

Its based on Ubuntu 8.04 LTS (long term support).  Unlike Ubuntu, it has the Medibuntu software repository enabled by default and automatically loads many proprietary drivers when the live CD boots.  I have not tested this version on the Broadcom chip set since I no longer use Broadcom based cards.  But an older version of gOS did recognize and run an older Broadcom wireless card.  Anyway, it may be worth the download to see if it works.

Another plus, it also does a very good job of multimedia support out of the box.  Good luck.

Joe

---

### Post by __p1n__ on 2009-09-12
Perhaps give the ndis wrapper approach another try.  I was able to get my 4328 N-phys dual-band working with that.

Some details can be found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by coffeeaddict22 on 2009-09-13
Hi, 
I've got a Studio 17  with a Broadcom 4322 card, and it runs sweet.  It takes a bit of fiddling to set up (but that means the kids will have trouble too, so it's a feature, not a bug...) 

 To quote your post: 

description: Wireless interface
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth1
version: 01
serial: 00:26:5e:26:8a:01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11


The important bits in there are you've got a driver (it's the right one), and it's linking it to a logical name.  

You don't seem to be linking to the access point.  I'm not sure why; iwlist scan would tell you more, but you need to run it as sudo: ```
sudo iwlist scan
```  
If I had to guess, check your ESSID and the password to get on your network.
If that doesn't work, post the sudo iwlist scan results back; another nice network toy is nm-tool; it doesn't add much info, but it does bring it all in to one output.  It's part of the Gnome network manager, so won't help if you're on wicd (I think).  Again, in a terminal, type ```
nm-tool
```

---

### Post by nstein on 2009-09-13
here is the output of iwlist scan:

francois@francois-laptop:~$ sudo iwlist scan
[sudo] password for francois: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:F0:F8:07:29
                    ESSID:"Habs"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD790050F204104A0001101044000102103B000103104700101BF9CFC5D7C935E0B99B969959A2A43B1021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1E:58:06:67:25
                    ESSID:"SLEBUIS"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:21:29:E3:8E:B1
                    ESSID:"Fusion3"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-94 dBm
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A880002129E38EB11021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 04 - Address: 
                    ESSID:"didan"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 
                    ESSID:"CAM"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:19:5B:25:40:5E
                    ESSID:"**** yeah"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 
                    ESSID:"Xiotanet"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:13:10:77:AF:B8
                    ESSID:"marie"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-89 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 09 - Address: 00:22:6B:63:91:85
                    ESSID:"Cisco"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483932393833381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 10 - Address: 00:13:A3:03:97:7A
                    ESSID:"Daniel Opazo"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 11 - Address: 
                    ESSID:"mariefranck"
                    Mode:Managed
                    Frequency=2.472 GHz
                    Quality:5/5  Signal level:-32 dBm  Noise level:-91 dBm
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:22:A4:0E:74:41
                    ESSID:"BELL822"
                    Mode:Managed
                    Frequency=2.447 GHz (Channel
                    Quality:4/5  Signal level:-67 dBm  Noise level:-65 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 13 - Address: 00:14:6C:A0:3E:B8
                    ESSID:"MGUAY"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 14 - Address: 00:1C:F0:F7:E9:B7
                    ESSID:"adisa"
                    Mode:Managed
                    Frequency=2.francois@francois-laptop:~$ sudo iwlist scan
[sudo] password for francois: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:F0:F8:07:29
                    ESSID:"Habs"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD790050F204104A0001101044000102103B000103104700101BF9CFC5D7C935E0B99B969959A2A43B1021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1E:58:06:67:25
                    ESSID:"SLEBUIS"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:21:29:E3:8E:B1
                    ESSID:"Fusion3"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-94 dBm
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A880002129E38EB11021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 04 - Address: 
                    ESSID:"didan"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 
                    ESSID:"CAM"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:19:5B:25:40:5E
                    ESSID:"**** yeah"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 
                    ESSID:"Xiotanet"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:13:10:77:AF:B8
                    ESSID:"marie"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-89 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 09 - Address: 00:22:6B:63:91:85
                    ESSID:"Cisco"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483932393833381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 10 - Address: 00:13:A3:03:97:7A
                    ESSID:"Daniel Opazo"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 11 - Address: 
                    ESSID:"mariefranck"
                    Mode:Managed
                    Frequency=2.472 GHz
                    Quality:5/5  Signal level:-32 dBm  Noise level:-91 dBm
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:22:A4:0E:74:41
                    ESSID:"BELL822"
                    Mode:Managed
                    Frequency=2.447 GHz (Channel 10)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-65 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 13 - Address: 00:14:6C:A0:3E:B8
                    ESSID:"MGUAY"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-91 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 14 - Address: 00:1C:F0:F7:E9:B7
                    ESSID:"adisa"
                    Mode:Managed
                    Frequency=2.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-94 dBm
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010416A62D6CC113DFEB3B2A259F4CA99841021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020004
                    Encryption key: on
                    Bit Rates:1 Mb/s

pan0      Interface doesn't support scanning.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-94 dBm
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010416A62D6CC113DFEB3B2A259F4CA99841021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020004
                    Encryption key: on
                    Bit Rates:1 Mb/s

pan0      Interface doesn't support scanning.

My network is "mariefranck" and the encryption is off because I'm using MAC address filtering. But the odd thing is that I'm not recieving any DHCPOFFERS from my router... My eht0 connection is working fine. So the real question is why my wireless connection is not recieving an address ?!

thx

---

### Post by coffeeaddict22 on 2009-09-13
You live in a busy part of the world...
Might be worth resetting the router, and/or try changing the channel.  If I had to guess, you've got a conflict.  Googling around, changing either channel or ESSID may solve the problem.  
Also, there's been an issue with one router/wireless card pair that's fixed in the Karmic distribution (if you're feeling brave).

---

### Post by nstein on 2009-09-14
yeah maybe i'll give it a try !

---

### Post by superm1 on 2009-09-14
If you have it set to a European only channel, try switching to one of the "common" channels.  These cards will only connect to the "common" channels.

---

### Post by nstein on 2009-09-14
Solved FINALLY !

The problem was that by default, there was some option enabled on my router. There was one named "Always broadcast (compatibility for some DHCP client)" and it was checked. 
So just like that, for fun I unchecked it, and you know what, IT WORKED ! I even downloaded wireshark to see what was going on on my network and usually my eth1 interface sent DHCP discovery signal and never got a response, now I send only 1 and I get an address.

wow, more than 5 days for a freakin' checked option... what do you know ! ;)

---

### Post by hubertofliege on 2009-10-09
It sounds like you tried a lot of things before you changed your router setting.  My friend is having similar problems, but I don't believe the router is the problem.  I think one of the things you did before you altered your router was the step which fixed it.  Any suggestions?

---

