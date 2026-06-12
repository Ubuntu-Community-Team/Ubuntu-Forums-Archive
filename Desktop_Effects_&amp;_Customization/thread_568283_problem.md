---
title: "problem"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by masklove on 2007-10-05
I have problem with ubuntu 7.1 beta 
i install it from 3 dats in the first he work very good in screen resolution 
1280*1024  but I make restart and I found he work with 1140*1140 it is very unusual number i try to make it 1280*1024   again but I didn't found any number but 640*480 I make restart alot of time but no use 
I need your answers please 
VGA 128 
Motherboard Gigabyte 945
Cpu  1.6 dual core 
Ram 512

---

### Post by masklove on 2007-10-06
no one give me answer Why??!!!!!!!!!!
:(:(:(:                 :confused::confused::

---

### Post by trak87 on 2007-10-06
You could try this at a terminal window:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select the resolutions you want when you get to that point.

---

