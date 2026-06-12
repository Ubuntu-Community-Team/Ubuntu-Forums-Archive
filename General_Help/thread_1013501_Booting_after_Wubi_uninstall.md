---
title: "Booting after Wubi uninstall"
date: 2008-12-16
forum: General Help
---

### Post by ident4 on 2008-12-16
HI

Just uninstalled Wubi after giving it a little try.

One small problem. 
Now when I start Windows I get the screen asking which operating system I want - XP or XP Recovery *whatever*.
I never used to get this - it would just start right away.
How do I bypass this screen?

Sorry - know this is more of an XP question than Ubuntu, but since Wubi did it...


thanks

---

### Post by ago on 2008-12-19
control panel > system > advanced > startup and recovery

---

### Post by ident4 on 2008-12-19
> **ago said:**
> control panel > system > advanced > startup and recovery

Hi

When I do that I get:
Time to display list of operating systems: 15 secs
Time to display recovery options when needed: 30 secs

When I click to manually edit startup options I have:

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcon
```

---

