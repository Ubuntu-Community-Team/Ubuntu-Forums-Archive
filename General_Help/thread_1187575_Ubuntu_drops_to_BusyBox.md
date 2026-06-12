---
title: "Ubuntu drops to BusyBox"
date: 2009-06-14
forum: General Help
---

### Post by GSZX1337 on 2009-06-14
When I attempt to boot into Ubuntu, I am greeted with a text prompt saying:

```
Gave up waiting for root device common problems
-Boot args (cat/proc/cmdline)
-check rootdelay = (did the system wait long enough?)
-check root < (did the system wait for the right device?)
-Missing modules (cat/proc/modules; ls/dev

ALER! /dev/disk//by -uuid/c00412a5-a203-4d06-99cdd-98bf1b6067c3 does not exits
Dropping to a shell!
```

Is there any way I can fix this without formatting? (I have Win Vista installed aswell) Any help would be appreciated.

Thanks in advance,
~GSZX1337

---

### Post by GSZX1337 on 2009-06-14
bumpy

---

### Post by ExemplarUbuntu on 2009-06-15
I had a similar problem but no solution:

[http://ubuntuforums.org/showthread.php?t=1171186](http://ubuntuforums.org/showthread.php?t=1171186)

The machine is offering me the latest update but I don't want to risk using it becuase it might delete the working version of the kernel.

---

### Post by GSZX1337 on 2009-06-24
I booted into a version of Ubuntu with an earlier kernel, installed an update giving me the latest kernel, installed the 9.04 upgrade from the Cd I DLed and every thing works wonderfully now.

...I *really* hope this never happens again. If it did, I'd have to wait for a new kernel version, or format Ubuntu. :(

---

