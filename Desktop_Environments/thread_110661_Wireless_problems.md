---
title: "Wireless problems"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Ollan on 2005-12-31
I'd like to surf wireless on my second computer with Kubuntu 5.10. Before I installed Kubuntu I plugged in an RT2500 based wlan-card. I followed this guide: [https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo), but skipped all about WPA (I have WEP 64 bit). I configured /etc/network/interfaces and kWiFiManager. The computer never get an IP-address, but kWiFiManager finds the network. Where to search the problem?

---

### Post by HermanAB on 2005-12-31
If you want to tinker with WiFi, then you need to read some man pages - it will save you a lot of hair.  Read the man pages on dhclient, ipconfig and iwconfig.

You need to do something like this:
$ sudo su -
password
# dhclient wlan0

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

