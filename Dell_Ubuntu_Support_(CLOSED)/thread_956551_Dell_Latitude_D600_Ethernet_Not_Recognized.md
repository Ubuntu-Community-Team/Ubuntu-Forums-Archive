---
title: "Dell Latitude D600 Ethernet Not Recognized"
date: 2008-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maxplayer14 on 2008-10-23
I have searched but it seems most people have had no problem with the actual on-board Ethernet being recognized but most have issue with the wireless.

My wireless works great but the on-board Ethernet isn't recognized.  I did:

```
sudo lshw -C network
```

But the only thing it shows is the Wireless Interface.

Any suggestions?

Thanks,

J

---

### Post by Cannotcompute on 2009-02-11
I'm reviving this because I have the same problem. And yes, it is on in the BIOS.

---

### Post by ugm6hr on 2009-02-11
Is it seen in:
```
lspci
```

---

### Post by Cannotcompute on 2009-02-12
Same as the other guy, I tried that, nothing admits that it exists.

---

