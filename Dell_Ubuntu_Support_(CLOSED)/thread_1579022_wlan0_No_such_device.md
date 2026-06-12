---
title: "wlan0 No such device"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by believe99 on 2010-09-21
- ubuntu 10.04 

 - i already can connect to wireless 


iwconfig 

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
ifconfig wlan0 up
```

wlan0: ERROR while getting interface flags: No such device

```where is wlan0 ?
help

---

### Post by mikewhatever on 2010-09-21
It looks like your wireless interface is eth1 and not wlan0.

---

### Post by believe99 on 2010-09-21
~$ sudo airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
888    avahi-daemon
891    avahi-daemon
968    NetworkManager
1033    wpa_supplicant
9028    dhclient
Process with PID 9028 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)



~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


so whats the problem ?

---

### Post by Enigmapond on 2010-09-21
> **mikewhatever said:**
> It looks like your wireless interface is eth1 and not wlan0.

Actually mine is this...I did nothing to alter it when I installed Lucid. How do I get it to read right? Or rather how can I make eth1 wlan0 like it should??

---

### Post by mikewhatever on 2010-09-21
believe99, I am not an airodump guru, but you should probably look at the man pages for both airodump and airmon.
[http://linux.die.net/man/1/airmon-ng](http://linux.die.net/man/1/airmon-ng)
[http://linux.die.net/man/1/airodump-ng](http://linux.die.net/man/1/airodump-ng)

Enigmapond, eth1 is the right reading.O:)

---

