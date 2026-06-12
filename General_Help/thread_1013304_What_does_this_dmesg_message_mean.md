---
title: "What does this dmesg message mean?"
date: 2008-12-16
forum: General Help
---

### Post by boterbram on 2008-12-16
running 8.10 64-bit on a hp compaq 8510w with vmware 2.0 and iwlagn homecompiled drivers, need more info just ask

This is my dmesg message i've been having some time now and seems to significantly slow down my wlan connection, but not my wired connection, although messages appear when using either one.

```
[  351.545247]    groups: 0-1
[  352.868286] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[  352.868596] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[  412.484366] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37773 DPT=161 LEN=54 
[  412.484737] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37773 DPT=161 LEN=54 
[  413.548228] ppdev0: registered pardevice
[  413.596108] ppdev0: unregistered pardevice
[  413.884500] ppdev0: registered pardevice
[  413.932407] ppdev0: unregistered pardevice
[  416.869193] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[  420.041519] ppdev0: registered pardevice
[  420.089281] ppdev0: unregistered pardevice
[  426.872239] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[  656.872205] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[  656.872437] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[  656.872674] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[  666.872227] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[  718.343930] Inbound IN=eth0 OUT= MAC=00:1f:29:7b:c2:a2:00:14:bf:42:54:9a:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=368 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=53608 LEN=348 
[  720.347554] Inbound IN=eth0 OUT= MAC=00:1f:29:7b:c2:a2:00:14:bf:42:54:9a:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=358 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=53608 LEN=338 
[  722.350595] Inbound IN=eth0 OUT= MAC=00:1f:29:7b:c2:a2:00:14:bf:42:54:9a:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=360 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=53608 LEN=340 
[  724.354260] Inbound IN=eth0 OUT= MAC=00:1f:29:7b:c2:a2:00:14:bf:42:54:9a:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=296 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=53608 LEN=276 
```

thanks in advance!

---

### Post by spiderbatdad on 2008-12-16
It looks like it is trying to configure ethernet devices for 2 virtual machine accounts you have running.

---

### Post by boterbram on 2008-12-18
Uhm ok but is it bad/do I need to fix it?

---

