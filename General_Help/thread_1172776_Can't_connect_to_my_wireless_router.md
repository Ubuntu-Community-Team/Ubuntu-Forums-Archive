---
title: "Can't connect to my wireless router"
date: 2009-05-28
forum: General Help
---

### Post by The Jinx on 2009-05-28
Hi,

I purchased a Dell Vostro A90 (aka Dell Mini 9) and I am having trouble connecting to my wireless connection. Although I am able to connect to my neighbors wireless connection without a problem. At first I thought this was a problem with the Dell Ubuntu that it came shipped with, but I am also unable to connect to my wireless router with a Live USB distro of 9.04. I managed to connect to my wireless router from the same Live USB on my Dell 1420n.

Also i disabled all types of security and mac address filtering on my router just to make things easier

Any instructions? please help


Thanks.
The Jinx

---

### Post by The Jinx on 2009-05-29
Bump? Please any help?

---

### Post by ActiveFrost on 2009-05-29
You can't connect or you don't see it in your wireless list ?

---

### Post by The Jinx on 2009-05-29
I can't connect. I'll see my wireless modem on the selectable list of connections but it just won't connect for some reason. 

In addition, I have a Verizon Westell 327w Wireless modem. IDK if this information will help. I also cannot connect to my cousin's wireless network who uses the same modem

---

### Post by Carl H on 2009-05-29
Open a terminal and type

```
iwconfig
```

and post the output on here

---

### Post by The Jinx on 2009-05-29
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr: off
          Power Managementmode:All packets received
          Link Quality=2/5  Signal level=-73 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0



this is what i get when i am trying to connect to my wireless modem

---

### Post by coffeecat on 2009-05-29
> **The Jinx said:**
> I can't connect. I'll see my wireless modem on the selectable list of connections but it just won't connect for some reason. 

You haven't got MAC address access control enabled, have you? I once did this, forgot about it, bought a netbook and wondered why it wouldn't connect. It took a frustrating hour for the penny to drop. :oops:

---

### Post by The Jinx on 2009-05-29
I do, but I added my MAC address to the allowed list. In addition, when i disabled MAC filtering and all sorts of security and SSID hiding i was still unable to connect to my modem

---

### Post by The Jinx on 2009-05-29
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:78:E5:A7   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr: off
          Power Managementmode:All packets received
          Link Quality=2/5  Signal level=-73 dBm  Noise level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:129  Invalid misc:0   Missed beacon:0


Here is an updated copy of my iwconfig when connected to my **neighbor's** wireless router

---

### Post by The Jinx on 2009-05-30
help?

---

