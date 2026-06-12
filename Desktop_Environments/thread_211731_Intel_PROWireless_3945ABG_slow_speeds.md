---
title: "Intel PRO/Wireless 3945ABG slow speeds"
date: 2006-07-08
forum: Desktop Environments
---

### Post by djoelsson on 2006-07-08
Hello,

I'll try to make this as succinct as possible.  I have an old Linksys wireless router (802.11b), a Sony laptop, and a homebuilt desktop.  Both are running Dapper and connect wirelessly without problems.  I usually get a speed around 3Mbps.

I just bought a new laptop (Toshiba Satellite A105) with a Intel PRO/Wireless 3945ABG chipset.  It's a core duo so I installed the 686 kernel.  I can now only connect with around 300 kBps.  A direct connection is as fast as the other computers.  The wireless works fine in Windows XP on the same laptop.

I have tried turning off IPv6, ndiswrapper, and changing the settings on my router, but nothing seems to work.

iwconfig give me the following:

eth1      IEEE 802.11b  ESSID:"dansnetwork"
          Mode:Managed  Frequency:2.462 GHz  Access Point:00:06:25:9A:1F:7C
          Bit Rate:11 Mb/s   Tx-Power:14 dBm
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=86/100  Signal level=-46 dBm  Noise level=-47 dBm
          Rx invalid nwid:0  Rx invalid crypt:52  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10971   Missed beacon:0

As you can see, the "invalid misc" number is very high.  My other laptop has a 0.

Any ideas?

Thanks for your help!

Dan

---

### Post by djoelsson on 2006-07-08
Sorry, I didn't see the wireless support forum earlier.

I posted this there.  Please ignore.

Dan

---

