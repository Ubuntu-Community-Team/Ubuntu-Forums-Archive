---
title: "Cannot seem to install wireless drivers"
date: 2008-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by crabpot8 on 2008-06-15
Hi. I am new to Ubuntu, and really liking it. I have a latitude D620 that I am trying to use to test WEP cracking on a FON router. I can use airodump-ng to capture packets and filter, so I can get my card into moniter mode fine. I cannot, however, inject any packets. 

I am a complete newbie, so I have been reading man pages out the wazoo. 

airdriver-ng lists these three drivers - one of which I think will work (not sure which one)
11. Intel Pro Wireless 3945 A/B/G - IEEE80211
12. Intel Pro Wireless 3945 A/B/G - raw mode
13. Intel Pro Wireless 3945 A/B/G - mac80211

problem is, when I try to install, I get these problems
$sudo airdriver-ng install 13
Driver "Intel Pro Wireless 3945 A/B/G" specified for installation.
DI_DRIVERPATH1[13] isn't set, you need at least one driver source!
Running "depmod -ae"...
Failed to install the driver.

So, obviously I am needing something, but i dont see a reference anywhere as to what. 

So, any info/pointing in the right direction would be awesome, or if someone knows if any of those three drivers will do the trick please let me know. Below I will post some info on the current setup of my system

crab


using Hardy Heron

:~$ sudo airdriver-ng detect (PS not sure why the same one seems to show up twice - what does 'device' actually mean? the device driver? Its talking about the same card, so that was the only thing I could think of)

Found "Intel Pro Wireless 3945 A/B/G" device: (ipw3945)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Found "Intel Pro Wireless 3945 A/B/G - raw mode" device: (ipwraw)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Found "Intel Pro Wireless 3945 A/B/G" device: (iwl3945)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


PCI devices (generic detection):
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

