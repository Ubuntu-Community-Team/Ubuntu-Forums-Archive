---
title: "Mini 9 Silent Wireless Disconnects"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ryxxui on 2008-11-07
I have Dell Mini 9, but I am encountering some relatively annoying wireless issues.
I made a clean install of Intrepid the other day.  The wireless for me does not work by default; I have to download and build the compat-wireless packages.  I am using the ath5k drivers, and my wireless appears to work fine.  However, my internet only appears to work in "bursts"- a page will load, then stall for a minute, and then load a bunch at once, and then stall some more.  The network manager program does not register that I am not connected to the wireless network anymore.  However, running dmesg in the terminal produces a repeating series of wireless errors:
```

[ 1898.640114] wlan0: No ProbeResp from current AP 00:1f:33:e4:5b:f6 - assume out of range
[ 1899.755643] wlan0: direct probe to AP 00:1f:33:e4:5b:f6 try 1
[ 1899.758673] wlan0 direct probe responded
[ 1899.758719] wlan0: authenticate with AP 00:1f:33:e4:5b:f6
[ 1899.765148] wlan0: authenticated
[ 1899.765194] wlan0: associate with AP 00:1f:33:e4:5b:f6
[ 1899.768970] wlan0: RX ReassocResp from 00:1f:33:e4:5b:f6 (capab=0x431 status=0 aid=3)
[ 1899.768996] wlan0: associated

```
This series of commands repeats about every 40 seconds, and corresponds directly to the times which I cannot receive any information.  Does anyone have any ideas as to why I may be having this issue?  I have seen it happen on multiple secured and unsecured wireless networks.  I appreciate the help.

---

