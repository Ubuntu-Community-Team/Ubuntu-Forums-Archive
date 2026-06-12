---
title: "Wired Internet (7.10, ps3) help?"
date: 2009-06-23
forum: General Help
---

### Post by MasterZURG on 2009-06-23
I just got an Ethernet cable and plugged it in to my ps3 and router (linksys) and the router works fine. I dont have any idea what to do or how to configure it. Can someone walk me through it? im a noob with any linux.

---

### Post by Iowan on 2009-06-23
I must have missed the problem... From your title, I can assume you have a 7.10 machine (like I'm on), and I presume it isn't connecting? 
Or is the problem with router configuration?
 My */etc/network/interfaces*:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

---

