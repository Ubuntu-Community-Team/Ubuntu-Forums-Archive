---
title: "How to disable fonts antialiasing in Qt appliations in GNOME?"
date: 2009-09-04
forum: Desktop Environments
---

### Post by przemnet on 2009-09-04
Hi,

I'm using Ubuntu 9.04 with GNOME and I'm trying to disable aa in apps like Opera, Skype or Kaffeine. I disabled it in Qt4 settings in System -> Preferences (equivalent of qtconfig entered in terminal) and also put the following statements into fonts.conf file:

```
<match target="pattern"> 
    <edit name="antialias" mode="assign"><bool>false</bool></edit> 
</match> 
<match target="pattern"> 
    <edit name="antialias" mode="assign"><bool>false</bool></edit> 
</match>
```

but fonts antialiasing is still present in Qt applications.

Can anyone help me to solve this problem?

Thanks in advance ;-)

---

### Post by deviato on 2010-08-23
Edit your ~/.kde/share/config/kdeglobals
Insert these lines:
[General]
XftAntialias=false
XftHintStyle=hintmedium
XftSubPixel=none

---

