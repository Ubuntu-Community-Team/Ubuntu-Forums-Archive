---
title: "strange gDesklet error"
date: 2005-03-31
forum: Desktop Environments
---

### Post by NeoChaosX on 2005-03-31
Having some trouble with some desklets from the warty universe repo. When I try to start some desklets (specifically, the LT Candy ones), it won't open and I instead get an error message showing me this:

```
Traceback (most recent call last):
  File "/usr/lib/gdesklets/factory/SensorFactory.py", line 86, in create_sensor
    sensor = module.new_sensor(args)
  File "/usr/share/gdesklets/Sensors/LTVDisk/__init__.py", line 83, in new_sensor
    def new_sensor(args): return apply(LTVDisk, args)
  File "/usr/share/gdesklets/Sensors/LTVDisk/__init__.py", line 36, in __init__
    for i in libdesklets.disk.get_partitions():
AttributeError: 'module' object has no attribute 'disk'
```

Anyone know what's going on and how to fix it?

---

### Post by Nis on 2005-03-31
Most of the old desklets, specifically the psi desklets, stopped working after gDesklets 0.33 came out.  This also affected many of the LT-Candy desklets.  I would suggest not installing gdesklets-extras and just download and install the displays you want from gdesklets.gnomedesktop.org.  There is a small change you need to make in TilingImage.py (do a slocate for it) and then you can use many of the cool SideCandy displays.  A lot of the displays are going towards only supporting gDesklets 0.34 since many useful changes have been introduced in 0.34.  You could also go the route of compiling 0.34 yourself. :)

---

