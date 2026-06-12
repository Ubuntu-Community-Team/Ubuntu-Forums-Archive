---
title: "Disable Latitude 2100 network activity light"
date: 2010-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chris1274 on 2010-08-01
For those using the Dell Latitude 2100 netbook, has anyone succeeded in disabling the network activity light? It just seems like something that *should* be easy to do, but I've scoured Google and no Ubuntu users have been able to do it. I tried adding the following to my /etc/rc.local file:
```
sudo iwpriv eth1 set_leddc 0
```but it doesn't do anything. In fact, I entered that command when logged in as root and it still doesn't work.

Any other suggestions?

---

### Post by djk44883 on 2010-08-04
I have a latitude 2110 and there is an option in the bios settings to disable it. 

It's likely the 2100 has a similar setting.   Hit F12 when you first power up.  Then choose bios settings.

---

### Post by Chris1274 on 2010-08-24
Unfortunately there's no similar BIOS option for the 2100.

---

