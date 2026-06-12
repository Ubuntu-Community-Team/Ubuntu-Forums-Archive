---
title: "C400 with Feisty; no WPA option"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by g00ner on 2007-06-05
Anyone know how to get WPA working on Feisty with a C400. Wireless network works great without encryption, but would like to get WPA working.

Thanks in advance

---

### Post by PKraszewski on 2007-06-05
C400/C500 have add-on WiFi cards. Please state, which model of WiFi card is installed. Command **lspci** should give you lines like that:

02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

please post your output.

---

### Post by g00ner on 2007-06-05
I will post the output when l get back home. I belive it is a Dell Truemobile 1150 which l understand is a rebranded orinoco card.

---

### Post by g00ner on 2007-06-05
ok l have the following

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (Rev 04)
00:02.0 VGA Compatible controller: Intel Corporation 82830 CGC (Chipset Graphics Controller) (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC (Chipset Graphics Controller)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI Bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA Bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE Interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI410 PC card Cardbus Controller (rev 02)
02:03.0 CardBus bridge: Texas Instruments PCI410 PC card Cardbus Controller (rev 01)

i guess 02:01 or 02:03 is the wi-fi card...?

---

### Post by PKraszewski on 2007-06-06
No, 02:01 and 02:03 are controllers of PCMCIA slot. Strange - I don't see any WiFi cards over there... Is your card PCMCIA or miniPCI?

---

### Post by PKraszewski on 2007-06-06
Oh, by the way - did you check [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")?

---

### Post by g00ner on 2007-06-06
it is definetly not pc card based, so it must be miniPCI

here is a link to a picture of it [http://images.google.co.uk/imgres?imgurl=http://eduroam.cz/lib/exe/fetch.php%3Fw%3D%26h%3D%26cache%3Dcache%26media%3Dcs:uzivatel:hw:karty:dell-truemobile-1150.jpg&imgrefurl=http://eduroam.cz/doku.php%3Fid%3Dcs:uzivatel:hw:karty:truemobile_11xx&h=1016&w=450&sz=180&hl=en&start=19&um=1&tbnid=pC8TmvDgyqyO-M:&tbnh=150&tbnw=66&prev=/images%3Fq%3Dtruemobile%2B1150%26start%3D18%26ndsp%3D18%26svnum%3D10%26um%3D1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3DsaY%26sa%3DN](http://images.google.co.uk/imgres?imgurl=http://eduroam.cz/lib/exe/fetch.php%3Fw%3D%26h%3D%26cache%3Dcache%26media%3Dcs:uzivatel:hw:karty:dell-truemobile-1150.jpg&imgrefurl=http://eduroam.cz/doku.php%3Fid%3Dcs:uzivatel:hw:karty:truemobile_11xx&h=1016&w=450&sz=180&hl=en&start=19&um=1&tbnid=pC8TmvDgyqyO-M:&tbnh=150&tbnw=66&prev=/images%3Fq%3Dtruemobile%2B1150%26start%3D18%26ndsp%3D18%26svnum%3D10%26um%3D1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3DsaY%26sa%3DN)

---

### Post by chili555 on 2007-06-07
Not every wireless chipset supports WPA. You can find out with:```
sudo iwlist eth1 key
```You might get output like:```
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: 096C-XXXX-XXXX-XXXX-XXXX-FE (104 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:restricted
          Authentication capabilities :
                WPA
                WPA2
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0xBF828768
          Current cipher_pairwise:0xBF828768
          Current cipher_group:0xBF828768
```Sustitute your wireless interface, if it's not eth1. Looks like my card *does* support WPA. As far as I know, there is no way to make an older card that was not designed to support WPA do so.

---

### Post by g00ner on 2007-06-07
when l had winxp on the c400, if l used the dell driver it only supported wep, but if l used the orinico driver l could get wpa working

---

### Post by PKraszewski on 2007-06-08
I *might* suggest ndiswrapper. This solved my problems with RT2500 card denying co-operaion with high-level configuration tools. But still - as the card looks like miniPCI,  it must be visible in lspci. As it is not, something wrong is happening...

---

