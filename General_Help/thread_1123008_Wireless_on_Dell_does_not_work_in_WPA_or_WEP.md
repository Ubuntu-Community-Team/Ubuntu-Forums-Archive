---
title: "Wireless on Dell does not work in WPA or WEP"
date: 2009-04-11
forum: General Help
---

### Post by landersohn on 2009-04-11
I am running Hardy 8.04 on Dell Latitude 420 and I am having problems connecting to wireless networks which are configured for WPA or WEP. WPA2 works just fine.
The network card driver is iwl3945.

The bug database is of no help since I tried all suggested fixes (driver version, NetworkManager latest version,....).
Does anybody have any ideas?

---

### Post by tommcd on 2009-04-11
I don't use WPA; but to connect to a WEP connected network run these commands in terminal:
```
iwlist wlan0 scanning
```
This will verify that your wireless card sees the access point.
```
ifconfig
```
This will tell you what your wireless device is called. It is usually **wlan0**.
```
sudo iwconfig wlan0 essid your_essid
```
This will tell your wireless to connect to the AP's essid.
```
sudo iwconfig wlan0 key your_WEP_key
```
This will give your wireless device the AP's WEP key so you can connect.
```
sudo dhclient wlan0
```
This should get you an IP address.
```
ping www.google.com
```
If you get a response you are good to go!

It seems odd that you can connect to WPA2 and not WPA. 

And welcome to the Ubuntu forums!

---

### Post by landersohn on 2009-04-12
Thanks, I'll give that a try

---

