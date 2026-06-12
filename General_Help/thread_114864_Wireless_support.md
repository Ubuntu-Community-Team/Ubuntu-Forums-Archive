---
title: "Wireless support"
date: 2006-01-09
forum: General Help
---

### Post by abrovink on 2006-01-09
Anybody have a Prism Wifi card working in ubuntu 5.10?

Device manager:ISL3886 (PRISM Javelin/Prism Xbow)

[B]dmesg:
[/B][4294701.110000] Loaded prism54 driver, version 1.2

**lsmod:**
prism54                47752  0
firmware_class          9472  1 prism54

**iwconfig eth1:**
eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ifconfig eth1 up:**
SIOCSIFFLAGS: No such file or directory

What should i do next?

---

### Post by abrovink on 2006-01-10
Bump?

---

### Post by healychan on 2006-01-10
You haven't set the essid yet.

sudo iwconfig eth1 essid "Yours essid"

sudo ifup eth1

---

### Post by abrovink on 2006-01-10
[QUOTE=healychan]You haven't set the essid yet.

sudo iwconfig eth1 essid "Yours essid"

sudo ifup eth1[/QUOTE]

Thank you for the reply!
Am i wrong if i think that i can have ESSID set to any/off to scan for active AP:s?

---

### Post by healychan on 2006-01-10
[QUOTE=abrovink]Thank you for the reply!
Am i wrong if i think that i can have ESSID set to any/off to scan for active AP:s?[/QUOTE]

You can still scan AP with ESSID any/off

iwlist wlan0 scan

will list all AP in your area

---

