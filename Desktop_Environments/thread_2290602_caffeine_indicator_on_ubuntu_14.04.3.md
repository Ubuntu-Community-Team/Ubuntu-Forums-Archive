---
title: "caffeine indicator on ubuntu 14.04.3"
date: 2015-08-13
forum: Desktop Environments
---

### Post by Gijsbert_Wiesenekk on 2015-08-13
caffeine no longer works on 14.04.3 (I did not have this error on 14.04.2):

$ caffeine-indicator 
Traceback (most recent call last):
  File "/usr/bin/caffeine-indicator", line 176, in <module>
    caffeine = Caffeine()
  File "/usr/bin/caffeine-indicator", line 125, in __init__
    self.root = display.Display().screen().root
  File "/usr/lib/python3/dist-packages/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/usr/lib/python3/dist-packages/Xlib/display.py", line 62, in __init__
    display.Display.__init__(*(self, ) + args, **keys)
  File "/usr/lib/python3/dist-packages/Xlib/protocol/display.py", line 129, in __init__
    raise error.DisplayConnectionError(self.display_name, r.reason)
Xlib.error.DisplayConnectionError: Can't connect to display ":0": b'No protocol specified\n'

The root cause is an error in python-xlib. The temporary workaround is to issue

$ xhost +

before you launch caffeine-indicator.

Regards,
Gijsbert

---

### Post by kNKGbYy on 2015-11-25
+1

I can confirm this works for Caffeine 2.8 on ubuntu 14.04.3

Thanks a lot!

---

