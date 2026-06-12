---
title: "window maker: need help with wifi"
date: 2009-10-19
forum: Desktop Environments
---

### Post by daweefolk on 2009-10-19
In ubuntu I have madwifi installed to support my atheros wifi card. I'm trying out Window maker and I like it except the fact that I can't seem to get it to recognize my card. I can see the network devices "eth0", "lo", "wlan0", but not my card, "ath0". What do I need to do to allow ath0 to be seen?

---

### Post by kerry_s on 2009-10-19
wlan0 is wifi, what make you think its ath0?

---

### Post by daweefolk on 2009-10-19
when I boot into gnome, the network manager recognizes ath0 as my wireless card

---

### Post by kerry_s on 2009-10-19
do "sudo iwconfig" in the terminal & post the output.

---

### Post by daweefolk on 2009-10-19
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"08FX08016825"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by kerry_s on 2009-10-19
your wireless is wlan0
it has a essid of "08FX08016825"
so just:
**sudo dhclient wlan0**

and you should get connected.

---

### Post by daweefolk on 2009-10-19
here's the output of sudo dhclient wlan0:
```
twitch@twitch-laptop ~ $ sudo dhclient wlan0
[sudo] password for twitch: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3a:6f:74:2f
Sending on   LPF/wlan0/00:1f:3a:6f:74:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

```

---

### Post by kerry_s on 2009-10-20
so is your router set up with dhcp?

---

### Post by daweefolk on 2009-10-20
I believe it is, as it works fine when i choose gnome as the environment to boot into. I'm not on my laptop right now but when I am I'll check to see if I accidently disabled dhcp in window maker

Edit:
Okay I checked my settings and dhcp is enabled. I even tried it on a different network and had the same result.

---

### Post by kerry_s on 2009-10-20
is the "ESSID:"08FX08016825"" correct, meaning thats the router name?

you can do:
**sudo iwlist wlan0 scan**

see what it can see.

if you need to set the essid:
**sudo iwconfig wlan0 essid router-name**

replace "router-name" with the essid you want.

i do example:
**sudo iwlist wlan0 scan** <--shows the networks in range
**sudo iwconfig wlan0 essid newday** <--tell it to connect to
**sudo dhclient wlan0** <--sets up the dhcp lease for access

---

### Post by daweefolk on 2009-10-20
```
$ sudo iwlist wlan0 scan
[sudo] password for twitch: 
wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:A0:7C:37
                    ESSID:"08FX08016825"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=92/100  Signal level:-41 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 000C303846583038303136383235
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000056cbf3dc6
                    Extra: Last beacon: 1312ms ago
          Cell 02 - Address: 00:16:B6:D6:AE:8D
                    ESSID:"jgarza"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/100  Signal level:-87 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 00066A6761727A61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000556c4bc027
                    Extra: Last beacon: 1220ms ago
          Cell 03 - Address: 00:18:F8:5F:C5:00
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/100  Signal level:-97 dBm  Noise level=-100 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180204F5
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000192f0d0f8ac
                    Extra: Last beacon: 1308ms ago
          Cell 04 - Address: 00:11:50:38:FC:51
                    ESSID:"052603cs"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/100  Signal level:-85 dBm  Noise level=-102 dBm
                    Encryption key:on
                    IE: Unknown: 00083035323630336373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010001
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000066875177a4
                    Extra: Last beacon: 960ms ago

twitch@twitch-laptop ~ $ sudo iwconfig wlan0 essid 08FX08016825
twitch@twitch-laptop ~ $ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 4511
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3a:6f:74:2f
Sending on   LPF/wlan0/00:1f:3a:6f:74:2f
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.40 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.40 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.40
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.


```
still not working... It couldn't ping my router, as shown near the end of that code.

---

### Post by kerry_s on 2009-10-22
```
          Cell 01 - Address: 00:12:0E:A0:7C:37
                    ESSID:"08FX08016825"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=92/100  Signal level:-41 dBm  Noise level=-100 dBm
                    **Encryption key:on**
                    IE: Unknown: 000C303846583038303136383235
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000056cbf3dc6
                    Extra: Last beacon: 1312ms ago

```


that has encryption turned on so you need to also do the key.
what kind of encryption?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

