---
title: "n52 output key bindings"
date: 2009-08-13
forum: Gaming &amp; Leisure
---

### Post by Sticks_uk on 2009-08-13
been trying to set up key binding with my n52 got the basic stuff working but need to find out the exact keys my n52 is bound to by default so i can re map them I have tried to run

cd /home/greengator/.config/pystromo
./pystromo-remap.py -m output.map -v

but get 

Traceback (most recent call last):
  File "./pystromo-remap.py", line 51, in <module>
    output = devices.OutputDevice()
  File "/home/greengator/.config/pystromo/lib/devices.py", line 665, in __init__
    self.node = ioctl.OutputNode()
  File "/home/greengator/.config/pystromo/lib/ioctl.py", line 237, in __init__
    raise LookupError ('no uinput device-nodes found')
LookupError: no uinput device-nodes found

some keys are bound to arrow keys and tab keys so do not know how to set this up

thanks in advance

---

