---
title: "the mana world"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by SLEEPER_V on 2009-12-13
got this error.  know what it means?

> oneal@obama:~$ tmw
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xad
  Serial number of failed request:  115
  Current serial number in output stream:  117


---

### Post by SLEEPER_V on 2009-12-13
no advice?

---

### Post by Perfect Storm on 2009-12-14
> X Error of failed request: BadValue (integer parameter out of range for operation)

Means that the game is starting up in a resolution that your system isn't set up for or can't handle.

---

### Post by Bjørn on 2009-12-14
You'll probably want to disable full screen mode by either editing ~/.tmw/config.xml or by erasing that file. If you go for editing, set the "screen" variable to 0.

---

### Post by SLEEPER_V on 2009-12-14
thanks guys.  Perfect!

---

