---
title: "rc.local needs delay to work..."
date: 2009-02-25
forum: General Help
---

### Post by jeanrocco on 2009-02-25
I was just trying get rc.local execute:
/usr/sbin/ethtool -s eth0 wol g

to enable WOL. Apparently this never gets executed, but if I run the script manually it works. I tried adding a delay like:
sleep 20 && /usr/sbin/ethtool -s eth0 wol g

and it worked, rc.local is this time executed the wol is enabled. 

It looks like rc.local is activated too early, the delay corrects that. Does anyone have an explanation for that ?

---

### Post by fragos on 2009-02-25
I put "kbdrate -r 15 -d 1000" in my rc.local set the keyboard delay and rate and it doesn't take either. Once running that command works in the terminal. Issueing commands before the device is ready appears to have been your problem but I doubt it was mine. There may be something else at play here. I'm going to try adding /sbin/kbdrate instead of kbdrate.

---

