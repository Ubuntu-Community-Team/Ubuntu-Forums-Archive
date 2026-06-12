---
title: "Wi-fi not working though wired connection works"
date: 2013-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nitesh_Sahay on 2013-09-13
[COLOR=#000000]I am completely new user getting into Ubuntu. I am facing wi-fi problem with my dell vostro machine. When I connect wi-fi, it gives a message saying Wi-fi connected but when I open the internet browser, it says cannot load the page. When I try the wired connection, it works absolutely fine. I tried to implement some solutions to similar question raised earlier as faithfully as was possible for me but it did not work.[/COLOR]

---

### Post by varunendra on 2013-09-13
Welcome to the forums Nitesh !

When connected via Wifi, please open a terminal (Ctrl+Alt+T) and post back the output of following commands -
```
nm-tool
ping -c4 google.com
ping -c4 8.8.8.8
```

And output of only "nm-tool" when you are connected via cable.

While posting the outputs, please use 'Code' tags to preserve the formatting of the outputs. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by Nitesh_Sahay on 2013-09-16
Dear Varun,

Thanks for the welcome! Here are the outputs.

**********************************************************************first  output**************************************************

```
mitu@mitu-Vostro-2420:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        AA:BB:CC:DD:EE:FF

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.130
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:45:C4:C0:2F:20

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        08:ED:B9:8A:00:03

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MH3_Grd_Floor1:  Infra, AC:67:06:1C:52:E8, Freq 2437 MHz, Rate 54 Mb/s, Strength 2
    DNA-2012:        Infra, 00:21:2C:D2:37:67, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WEP
    MH3_1st_Floor1:  Infra, AC:67:06:1C:62:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 5

```
**********************************************************************next output**************************************************

```
mitu@mitu-Vostro-2420:~$ ping -c4 google.com
ping: unknown host google.com
```

**********************************************************************next output**************************************************

```
mitu@mitu-Vostro-2420:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.105 icmp_seq=1 Destination Host Unreachable
From 192.168.1.105 icmp_seq=2 Destination Host Unreachable
From 192.168.1.105 icmp_seq=3 Destination Host Unreachable
From 192.168.1.105 icmp_seq=4 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3001ms
pipe 3
```

---

### Post by varunendra on 2013-09-17
See those smileys in your codes? That's because of posting it as normal text. Please edit the above post and wrap the output part within code tags (read the last line of my previous post).

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Oh, and don't forget the code tags, because this one is going to be a huge output ;)

---

