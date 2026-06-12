---
title: "utility to find out wifi signal strength"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tapas_mishra on 2010-05-21
I want to know if there is any utility that can help me to find out the signal strength which I am having on my wifi.At a few places where I am using wifi the signal strength is low.I want to give a proof of this to my sysadmins.

---

### Post by mellowtothemax on 2010-05-21
Type iwconfig at terminal. It shows statistics and info for the current connection.

---

### Post by tapas_mishra on 2010-05-23
This is output of iwconfig what does it tell about wifi signal strength.
```


 iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"HOSTEL"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:69:F2:A5:61   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-45 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1187  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
This output is at a point where I have good strength.

---

