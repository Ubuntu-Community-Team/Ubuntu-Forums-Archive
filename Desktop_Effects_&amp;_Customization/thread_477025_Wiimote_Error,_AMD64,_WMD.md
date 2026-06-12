---
title: "Wiimote Error, AMD64, WMD"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by BlahMan_of.Doom on 2007-06-17
I'm having problems with WMD..
```
$ sudo python WMD.py
Password:
uinput: Trying to open /dev/input/uinput as control device
uinput: Writing WIIMOTE_UUD
uinput: Registering 31 events
uinput: Creating device
uinput: initialized and ready
CONNECTING
Looking for Wiimote services at address 00:17:AB:36:09:52
Failure. We have not found that Wiimote.
Now trying to discover a willing Wiimote, please activate your Wiimote within 5 seconds.
Found 1 Bluetooth Devices!
Found a Wiimote at address 00:19:1D:27:8B:DA
Looking for Wiimote services at address 00:19:1D:27:8B:DA
Failure. We have not found that Wiimote.
Traceback (most recent call last):
  File "WMD.py", line 45, in <module>
    wmd = WMD()
  File "WMD.py", line 40, in __init__
    if wm.connect() and wm.setup():
  File "/home/sixthelement/Desktop/wmd-trunk/wmd/Wiimote/WMManager.py", line 21, in connect
    addr = self.backend.get_addr( )
  File "/home/sixthelement/Desktop/wmd-trunk/wmd/Wiimote/Backends/PyBlueZ.py", line 58, in get_addr
    log(DEBUG_INFO, "No luck finding Wiimote services.")
NameError: global name 'DEBUG_INFO' is not defined
```

I tried the solution in the other thread, but that does not work.

edit: video for example: [http://www.youtube.com/watch?v=ALqduQfm09c](http://www.youtube.com/watch?v=ALqduQfm09c)
Thank you.

---

### Post by BlahMan_of.Doom on 2007-07-20
I know there's someone here who knows what to do...

---

### Post by BlahMan_of.Doom on 2007-07-20
Okay I got it working, but how do I map buttons?

---

### Post by jdfreshwater on 2007-08-20
You map the buttons in the config.py file in the directory inside of the where you have WMD.

---

