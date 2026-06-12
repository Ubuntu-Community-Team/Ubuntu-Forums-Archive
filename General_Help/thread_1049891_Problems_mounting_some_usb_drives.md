---
title: "Problems mounting some usb drives"
date: 2009-01-25
forum: General Help
---

### Post by JMuffin on 2009-01-25
A while ago I lost the ability to mount usb drives. I would get the error "you do not have privilege to mount the volume". I figured out that editing a line in my fstab to say /dev/sdc instead of /dev/sdc1 restored my ability to mount usb drives. Fast forward to now and I am unable to mount my Sansa mp3 player. Messing around some more and I find out that if I change that line back to /dev/sdc1 I can mount the Sansa fine, but not any other usb drives. Any ideas how I might fix this or what's causing it? To sum up, the following line allows me to mount my Sansa and no other usb drives:
```
/dev/sdc1 /media/storage ext3 defaults,relatime 0 0
``` 

and this line allows me to mount all usb drives except the sansa:
```
/dev/sdc /media/storage ext3 defaults,relatime 0 0
```

It's nice to know that I have the ability to mount either of them, but would prefer not to have to edit my fstab between changing devices.

---

