---
title: "Where are the dns settings in new ubuntu"
date: 2009-05-17
forum: General Help
---

### Post by clownzy on 2009-05-17
I was just wondering where i can locate the dns settings to change them in the new ubuntu version?The location seems to have changed.
Thanks

---

### Post by spiderbatdad on 2009-05-17
/etc/resolv.conf

---

### Post by alphacrucis2 on 2009-05-17
> **clownzy said:**
> I was just wondering where i can locate the dns settings to change them in the new ubuntu version?The location seems to have changed.
Thanks

The network settings are controlled by the Network Manager applet. I believe the data gets stored via gconf in xml files under ~/.gconf/system/networking. From what I read you can stop Network Manager taking over an interface by hard coding it in /etc/network/interfaces.

My /etc/network/interfaces only has:

```
auto lo
iface lo inet loopback
```


Supposedly you can add something like:

```
auto eth0
iface eth0 inet dhcp

```

Is supposed to cause Network Manager to leave eth0 alone thus it reverts to the old setup. I haven't tried it myself though.

---

