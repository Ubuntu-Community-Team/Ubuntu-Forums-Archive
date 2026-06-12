---
title: "Mini 9 sample iwlist output"
date: 2009-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kakotako on 2009-12-27
Could someone be kind to execute

```
sudo iwlist eth1 scan
```

and post the result here. Wipe out the SSID numbers if you'd like.

I replaced the original Broadcom card that came with Dell Mini 9. I had written a script that parses the iwlist output but the formatting is slightly off with my new Intel card so the script no longer runs. 

It would help me see where the difference is by comparing the original card vs. the Intel card.

---

### Post by Zoot7 on 2009-12-27
iwlist is only to scan for wireless networks, it isn't going to work with ethX.

Normally what you do to connect wirelessly (assuming it's WPA1/2) is this (as root) :
```
ifconfig wlan0 up
wpa_passphrase <network name> <passphrase> > /etc/wpa_supplicant.conf
iwconfig wlan0 essid <network name>
wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf
dhclient wlan0 (if you're using dhcp)
```

Edit, BTW here's a **iwlist wlan0 scan** output for me:
```
mark@marks-rig:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:2A:F6:24:53
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"h0m3-wiF1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010a52e1c237
                    Extra: Last beacon: 119492ms ago
                    IE: Unknown: 000942616C6C797279616E
                    IE: Unknown: 010582848B960C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by kakotako on 2009-12-27
Thanks Zoot7. Is this on Mini 9 with factory installed Broadcom card?

I know what you're saying about eth1 interface but somehow on factory fresh Mini 9 with Broadcom card and wl driver the wireless interface is reported as eth1.

---

### Post by Zoot7 on 2009-12-28
> **kakotako said:**
> Thanks Zoot7. Is this on Mini 9 with factory installed Broadcom card?
No, it's from my home built desktop, which has an Atheros based wireelss card. Shouldn't really be any different to the mini 9 if the wireless is set up accordingly.

> **kakotako said:**
> I know what you're saying about eth1 interface but somehow on factory fresh Mini 9 with Broadcom card and wl driver the wireless interface is reported as eth1.
That's interesting. Maybe you could try a different driver? Either that or a reinstall, the OEMs have a habit of trashing the preinstalled OS's - Windows and Linux alike. But beyond that I can't really help you to be honest, i've generally avoided broadcom cards like the plague.

---

### Post by ugm6hr on 2009-12-28
Output on 9.04 / Mini 9:
```
eth1      Scan completed :
          Cell 02 - Address: 
                    ESSID:"xxx"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 
                    ESSID:"yyy"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:22:75:AC:B8:A6
                    ESSID:"RBP"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 05 - Address: 
                    ESSID:"zzz"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 
                    ESSID:"aaa"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

```

I've removed the addresses / ssids.

---

