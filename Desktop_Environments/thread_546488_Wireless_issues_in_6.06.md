---
title: "Wireless issues in 6.06"
date: 2007-09-08
forum: Desktop Environments
---

### Post by chicker on 2007-09-08
I'm sure this is a questions that gets asked a lot, but I couldn't find a solution from other threads.  Keep in mind also that I'm new to linux, so if there's something more you need to know, let me know, and tell me how to find it for you. 

The issue is this, I'm running Ubuntu 6.06 on a Compaq Evo N400c.  I'm using an IBM wireless card, 802.11b, it just seems like a generic model. Can't find a model name or anything. 

Until recently, the wireless connection was flakey but worked fairly well, I was having to do the sudo ppoeconf because of modem issues that required doing pppoe login manually every time.  We've fixed the issue and now, all the windows/mac computers are connecting automatically just fine, but the ubuntu machine isn't finding the network.  I've tried rebooting, taking the wireless card in/out, deactiving/activating in the networking window, restarting the modem, etc. 

I tried manually inputting the essid, to no avail.  It just doesn't find any access point. 

here's what comes up with iwconfig:

eth1 IEEE 802.11b  ESSID:"" Nickname:"HERMES I"
Mode:Managed  Frequency:2.457 GHz  Access Point: None
Bit Rate: 2 Mb/s Sensitivity: 1/3
Retry limit:4 RTS thr:off Fragment thr:off
Encryption key: off
Power management:off
Link Quality: 0/92 Signal Level = 134/153 Noise level=134/153
Rx invalid nwid:0 RX invalid crypt:0 RX invalid frag: 0
TX excess retries: 0 Invalid misc:0 Missed beacon:0

Any ideas? As I said, all the other computers are working fine, I tried using a different wireless card that was working on another laptop but it didn't work...so it must be a setting or something.

---

