---
title: "How to setup a wifi hotspot in Dell Vostro using ubuntu 12.04 &amp; Broadcom Wireless LAN"
date: 2012-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sevior on 2012-10-05
Hi, I need your help in setting-up my laptop to be a wifi hotspot. I already followed some tutorial but I still did not succeed. Im using a Dell vostro laptop and a Broadcom Wireless LAN controller. Here are some info that may help

```
lspci
```
```
12:00.0 Network Controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

```
iwconfig
```
```
wlan0  IEEE 802.11bgn ESSID:off/any
             Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
             Retry  long limit:7   RTS thr:off   Fragment thr:off
             Encryption key:off
             Power Management:on
```

```
iw list
```
```
Supported interface modes:
               * managed
               * monitor
```

This is a dual boot system - Windows 7 and Ubuntu 12.04. I tried installing Connectify in Windows and it did work but when i tried the hotspot in Ubuntu I wasn't able to broadcast any signal. Can my LAN accommodate such setup? 

Any help will be highly appreciated. I really need some. Thanks in advance :)

---

### Post by Sevior on 2012-10-05
I already figured out how this should work.

I installed a driver using the following steps:
System Settings > Additional Drivers > Broadcom STA wireless driver > enable button (below) > Restart laptop

It changed my "wlan0" to "eth1". and then I followed the steps here.
[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

Hope this helps :)

---

