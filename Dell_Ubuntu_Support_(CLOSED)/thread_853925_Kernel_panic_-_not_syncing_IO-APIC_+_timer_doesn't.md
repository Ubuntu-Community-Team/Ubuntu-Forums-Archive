---
title: "Kernel panic - not syncing: IO-APIC + timer doesn't work!"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Caponetta on 2008-07-09
Dimension C521
Ubuntu 7.10 Gutsy 64bit

I just installed 7.10 on a dell Dimension C521 via wubi.
I booted for the first time and it installed everyting properly. I booted for the second time (first real boot) and while loading kernals the folowing error occured```


Kernel panic - not syncing: IO-APIC + timer doesn't work!
```

Please help me, there has to be a fix for this.

---

### Post by forger on 2008-07-09
have you tried with the latest 8.04[COLOR="Red"]**.1**[/COLOR] cd?
it has better support for wubi
get it at [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu)

---

### Post by Caponetta on 2008-07-09
> **forger said:**
> have you tried with the latest 8.04[COLOR="Red"]**.1**[/COLOR] cd?
it has better support for wubi
get it at [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu)
8.04 does not support my wireless card (Net Gear WG11t)

---

### Post by forger on 2008-07-09
you mean with WEP it doesn't work, without WEP it works fine :)
try **ndisgtk** package and head to system > administration > windows wireless drivers
you find your driver's .inf file (usually inside a setup program)

[http://ubuntuforums.org/showthread.php?t=626499](http://ubuntuforums.org/showthread.php?t=626499)
[http://forums.debian.net/viewtopic.php?p=68058#68058](http://forums.debian.net/viewtopic.php?p=68058#68058)

---

### Post by Caponetta on 2008-07-09
> **forger said:**
> you mean with WEP it doesn't work, without WEP it works fine :)
try **ndisgtk** package and head to system > administration > windows wireless drivers
you find your driver's .inf file (usually inside a setup program)

[http://ubuntuforums.org/showthread.php?t=626499](http://ubuntuforums.org/showthread.php?t=626499)
[http://forums.debian.net/viewtopic.php?p=68058#68058](http://forums.debian.net/viewtopic.php?p=68058#68058)

Yes, i did that, and it does not work. It detects the hardware but it doesn't even give me the option to use wireless.

---

### Post by Caponetta on 2008-07-09
Im reinstalling 8.04.1, i think i made an error while downloading the driver. I'll keep you updated.

---

### Post by forger on 2008-07-09
please do :)

---

### Post by Caponetta on 2008-07-09
same problem. hardware found no option to connect via wireless.. :confused:

---

