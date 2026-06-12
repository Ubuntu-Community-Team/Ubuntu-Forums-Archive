---
title: "Wireless drivers issue for a new install on acer aspire 7100"
date: 2009-04-28
forum: General Help
---

### Post by draperdt on 2009-04-28
I am trying to install the wireless driver for a fresh install of xubuntu on a laptop. I followed these _[instructions]("http://ubuntuforums.org/showthread.php?t=25683")_[,]("http://ubuntuforums.org/showthread.php?t=25683") installed ndiswrapper, obtained the .sys and .inf files and installed it. Or atleast I am assuming I did. This is what I get from iwconfig

```
laptop:/etc/ndiswrapper/bcmwl5$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```I checked the .conf files in the etc/ndiswrapper/bcmwl5/ to make sure that it says RadioState|0.

When I issue ```
sudo modprobe ndiswrapper
```I get

```

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```lshw gives ```
 

-network:0 DISABLED 
description: Wireless interface
physical id:1
logical name: wlan0
serial: 00:16:ce:23:fa:be
capabilities: ethernet physical wireless
configuration: broadcast=ye multicast=yes wireless=IEEE 802.11bg
```I cant seem to find system-administration- menu on xubuntu to graphically enable it. What should I do next.

Thank you.

---

### Post by stef4001 on 2009-04-28
Hi I hade the same problem on the ultimate edition 2.1 I hade installed my .inf driver with ndiswrapper true commandline buth it dit not becom active then i installed the grafical interface for ndiswrapper dit it there and it workt fine its cald ndisgtk also i haven the packages ndiswrapper-utils-1.9 and ndiswrapper common

---

