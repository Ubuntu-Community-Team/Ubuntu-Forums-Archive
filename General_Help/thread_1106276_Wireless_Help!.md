---
title: "Wireless Help!"
date: 2009-03-25
forum: General Help
---

### Post by bluestreek on 2009-03-25
Enabling ath9k

To enable ath9k, you must first enable mac80211:

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

You can then enable ath9k in the kernel configuration under

Device Drivers  --->
  [*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 802.11n wireless cards support

I have no idea what this means or where these "Networking" or "Wireless" menu's are.  Also I am trying to setup Kismet and it says I have to set capture sources but im not sure how what to put in the format thing.

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
source=none,none,addme

Any help would be great.  I have Atheros card 928x In my laptop (At least thats what its called in device manager in windows)  Its wireless n.  I have Ubuntu 8.10 and ath9x is meant to be included in the kernel I think.

I think this is the wrong forums -- sorry :(((

---

