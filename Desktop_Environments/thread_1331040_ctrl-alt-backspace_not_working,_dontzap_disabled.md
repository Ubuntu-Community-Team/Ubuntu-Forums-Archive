---
title: "ctrl-alt-backspace not working, dontzap disabled"
date: 2009-11-18
forum: Desktop Environments
---

### Post by jmcgovern on 2009-11-18
I have run the 'dontzap --disable' command, and have verified the 'Option "Dontzap"  "false"' entry in my xorg.conf file.  however, the combination still does nothing.  This is in 9.04,

---

### Post by lidex on 2009-11-19
Did you install dontzap package and restart xserver or reboot?
That command should be run with sudo:
```
sudo dontzap --disable
```

---

