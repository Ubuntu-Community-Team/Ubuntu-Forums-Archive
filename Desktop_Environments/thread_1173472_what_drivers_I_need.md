---
title: "what drivers I need?"
date: 2009-05-29
forum: Desktop Environments
---

### Post by Zom-b on 2009-05-29
I think while trying to tweak my laptop a bit I messed something up, now it shows jiberish when I try to load it upo, so I just need to know what the default video drivers are and how to get them and how to see what video drivers I have isntalled so I can remove the culprti

---

### Post by Zom-b on 2009-05-29
actually I found what I needed to do by searching around the forums a bit more
```

sudo apt-get --purge remove xorg-driver-fglrx fglrx-control

sudo dpkg-reconfigure xserver-xorg

sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa libgl1-mesa-dri 

```

---

