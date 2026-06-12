---
title: "hdparm settings"
date: 2006-04-21
forum: Desktop Environments
---

### Post by arachn1d on 2006-04-21
Can someone tell me how to reset it? I used a guide and then realized it was from 2000 and I guess it made  it slower than faster.

If anyone can tell me how to reset it and then enable dma and some other good options let me know.


Thanks!

---

### Post by louis_nichols on 2006-04-22
well.... enabling dma is as easy as

```
$sudo hdparm -d 1 /dev/hdc
``` (assuming /dev/hdc is indeed the device you are trying to modify)

as for resetting previous settings and make new ones to be activated on boot... I dunno if deleting /etc/hdparm is safe. What you could try is a simple

```
$sudo dpkg-reconfigure hdparm
```

this should return everything to the way thins were before tweaking settings. Then, to set hdparm to enable dma at boot time, simply *sudo gedit /etc/hdparm* and add at the end the entry (again, assuming /dev/hdc is the device in question):

```
/dev/hdc {
dma=on
}
```

EDIT: well... in KDE that would actually be *sudo kedit /etc/hdparm*

---

### Post by fdoving on 2006-04-22
```

**kdesu** kedit /etc/hdparm.conf

```
Would be the Kubuntu way :)

- Frode

---

