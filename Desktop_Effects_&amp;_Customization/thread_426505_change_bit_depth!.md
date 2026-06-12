---
title: "change bit depth!"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by moguri1988MI on 2007-04-28
hi! I'm having trouble lately with Ubuntu (and specifically with Wine)
It so just happens that several programs running under Windows cannot run under Ubuntu despite having Wine installed. The error reported that I had to change the resolution from 24bit to 16 or 32bit.

Any hints on how to do that? :( 

Thanks in advance 

Moguri:KS

---

### Post by FuturePilot on 2007-04-28
```
gksudo gedit /etc/X11/xorg.conf
```

Go down to the Screen Section and find the line that says "Default Depth" Then Just change that number to what you want. Save, log out and restart X by <Ctrl><Alt><Backspace>

---

