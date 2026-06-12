---
title: "Wifi-radar died..."
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by boarder2k7 on 2007-07-30
I was using Wifi-radar on my Lattitude C6(40?)....... It was working fine, doing all as it should, then I shut the laptop off, and when I turned it back on, Wifi-radar was dead...

After poking for a bit, i went to open it in the terminal with "sudo wifi-radar".  It brings up....

dhclient3 --version 2>&1
Traceback (most recent call last):
   File "/usr/sbin/wifi-radar", line 1414, in <module>
      auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'


I have no clue what it means......... Help! lol

---

### Post by Frugoo Scape on 2007-07-30
Did you press fn + f2? That turns my wireless thing on and off.

---

### Post by boarder2k7 on 2007-07-30
Yeah, the card is on and working, its lights are on and  I can see networks with the network icon in the top right, but I cant connect.

B

---

### Post by walkerk on 2007-07-30
```
iwlist scanning
```

sometimes your card gets recognized differently.. 

sometimes eth1, sometime wlan0... you need to ensure that you have the right interface in the wifi-radar config file..

to assign a NIC by mac address do the following:
```
sudo gedit /etc/iftab
```

add the following line:
```
wlan0 mac 00:00:00:00:00:00 arp 1
```

where 00:00:00:00:00:00 is your mac address..

now ensure that interface is in your wifi-radar.conf:
```
sudo gedit /etc/wifi-radar.conf
``` 

should be something like:
```
interface=wlan0
```

hope this helped. of course you can always make the switch to [WICD]("http://wicd.sourceforge.net") which works similar wifi-radar but vastly improved..

---

