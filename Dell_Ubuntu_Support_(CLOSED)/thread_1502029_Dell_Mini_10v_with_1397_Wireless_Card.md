---
title: "Dell Mini 10v with 1397 Wireless Card"
date: 2010-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimHeckman on 2010-06-05
So,

I have a Dell Mini 10v with one of their 1397 Mini-Wifi Cards.  The unit connects to the internet just fine.

The issue I am having has to do with NetworkManager displaying signal strength. I can be sitting next to the router, and the notificaion icon has the red exlamation point acting as if it's not connected to a network properly.

Yet, when I jump into Windows it recognizes the signal strength flawlessly.

I mean...this is not a functionality issue.  But I'd like to be able to monitor my signal strength.

Anyone have any ideas what I can do to resolve this issue?

Edit: The router is a NETGEAR WNR3500v2 running DD-WRT Firmware.

Thanks,
Tim

---

### Post by mikewhatever on 2010-06-10
Can you post the output of the following:
nm-tool

---

### Post by TimHeckman on 2010-06-10
```
element@timheckman-netbook:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1  [Auto eLement] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        70:1A:04:95:DB:56

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    eLement:         Infra, 00:24:B2:C3:67:4E, Freq 2447 MHz, Rate 0 Mb/s, Strength 80 WPA2
    HPPAVILION:      Infra, 00:26:F2:1A:95:B8, Freq 2412 MHz, Rate 0 Mb/s, Strength 40 WPA WPA2
    jean carlos:     Infra, 00:23:97:06:E7:61, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WEP

  IPv4 Settings:
    Address:         192.168.0.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:ED:24:21

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


element@timheckman-netbook:~$ 
```

As I said, it connects to "eLement" just fine. But still shows red exclamation point.  It's odd.

---

### Post by mikewhatever on 2010-06-11
This is rather puzzling, as the output shows an IP address, but doesn't show which network it's connected to. That said, the signal strengths of the available networks are shown alright.

---

### Post by TimHeckman on 2010-06-11
Yeah, I tried messing around with it and have no clue.

And the funny thing is, when the notification shows up to tell me that I'm connected to a network...it displays the correct network name.

I guess I shouldn't jinx it as long as it connects.

---

### Post by mikewhatever on 2010-06-11
Was it like that from the start, on live cd/usb? Which version of Ubuntu are you on?
I have a mini 10 with apparently the same card, and it's been working well with Jaunty and Karmic.

---

### Post by TimHeckman on 2010-06-12
Hm, don't know if I ever checked running the LiveCD environment.  I'm using Lynx.

---

### Post by mikewhatever on 2010-06-13
Live cd or usb, it shouldn't matter. Haven't you used a usb stick to install Lucid Lynx?

---

### Post by TimHeckman on 2010-06-14
Yeah, but wiped it because I need it for something.

I'll pick up another one, and test it.  I've not tried it, but would there be any issues using a restricted driver?  I'm not sure how a Live Environment handles this...

---

