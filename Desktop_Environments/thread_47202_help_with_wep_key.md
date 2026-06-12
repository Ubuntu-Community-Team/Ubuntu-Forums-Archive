---
title: "help with wep key"
date: 2005-07-07
forum: Desktop Environments
---

### Post by jaross on 2005-07-07
It seems to expire in linux after about 24 hours.  I have to type it in again, before i can get the internet connection to work after that.  I type in the same one it used to have and it works all over again for another 24 hours, so I know my router isnt changeing the wep key.  also, I have 3 other computers that all have either windows or OSX and they all contuinue to work.  How do I get linux to do the same?

---

### Post by alastair on 2005-07-07
Do you have a single key configured, or a list? Some routers let you assign multiple keys and choose between them I believe.

The key is usually stored as an option in the main network config file /etc/network/interfaces.

For instance, for eth1 (wireless), you might have :

iface eth1 inet dhcp
wireless_essid <ESSID>
wireless_key <WEP KEY>
wireless_keymode restricted
wireless_ap <AP MAC>

---

### Post by jaross on 2005-07-07
I have one key for 4 sometimes 5 computers and it has been the same since we got the router.  all of the otehr computers withought linux continue to work just fine.  I talked to this really nice guy on irc and he helped me set up a sceduler that would ping my router every hour to hopefully keep the connection up.  if that doesnt work, i will report back here.

---

