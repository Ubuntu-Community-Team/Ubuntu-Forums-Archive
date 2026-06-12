---
title: "Problem with Wireless Madwifi"
date: 2006-01-10
forum: Desktop Environments
---

### Post by gomj0001 on 2006-01-10
Hi:
I have installed Madwifi and everything seems to have worked ok
if i type
iwconfig

i get 

> lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Melrose1012"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:E5:E7:8B
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:454  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:27  Invalid misc:27   Missed beacon:15

sit0      no wireless extensions.


Which means that my card is installled but when i go to system settings my wireless card shows disabled and when i clic re-enable it sits there and then goes back to being disabled. Also if i run 

> ifconfig ath0 up

 i get 
> 
SIOCSIFFLAGS: Permission denied


Any help is a ppreciated. I am running with root privileges so there is no problem with permissions. Thanks

---

### Post by DeadEyes on 2006-01-11
Do you need to be admin to run that command?
```

sudo ifconfig ath0 up

```

---

