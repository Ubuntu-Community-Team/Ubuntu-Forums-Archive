---
title: "Excessive retries when using Wifi"
date: 2006-07-19
forum: Desktop Environments
---

### Post by avinashm on 2006-07-19
Hi all,

I'm using a small USB Wifi adapter with a desktop PC running Dapper. iwconfig tells me:



wlan0 802.11b/g NIC  ESSID:"XXXXX"
          
Mode:Managed  Frequency=2.457 GHz  Access Point: XXXXX
Bit Rate:54 Mb/s
Retry off   RTS thr=2432 B   Fragment thr off
Power Management off
Link Quality=80/100  Signal level=41/100  Noise level=0/100
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:68
Tx excessive retries:4712  Invalid misc:0   Missed beacon:0



Note that the "Tx excessive retries" is very large even though the "Link Quality" is very good. According to the iwconfig man page, "Tx excessive retries" is the number of packets that the hardware (presumably my USB Wifi adapter) failed to deliver (presumably to the Access Point).

My questions are:

(1) Is it normal to have a large "Tx excessive retries"?

(2) If not, what might be happening and how to solve the problem?

Thanks a lot :)

---

