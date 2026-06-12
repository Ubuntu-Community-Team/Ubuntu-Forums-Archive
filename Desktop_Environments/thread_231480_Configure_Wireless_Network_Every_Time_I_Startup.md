---
title: "Configure Wireless Network Every Time I Startup"
date: 2006-08-07
forum: Desktop Environments
---

### Post by albaine on 2006-08-07
Hi, I recently installed Ubuntu 6.06 on my Dell D600 laptop and am loving it.

My wireless works well, but very time I restart my computer, I have to reconfigure the WEP key.  I go to System > Administration > Networking; I highlight the wireless network and click Properties; and I enter the ESSID, key type (ASCII), and the WEP key.

Does anyone know how I can configure these settings to default to my home wireless network so I don't have to re-configure every time I restart?  Thanks in advance for any help.

Andrew

---

### Post by jrattner on 2006-08-07
Specify the SSID + Key in /etc/interfaces

---

### Post by albaine on 2006-08-07
How do I do that?

---

### Post by jrattner on 2006-08-07
Here is an example of a wireless config in /etc/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed
```

Refer to [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") for the full scoop.

---

