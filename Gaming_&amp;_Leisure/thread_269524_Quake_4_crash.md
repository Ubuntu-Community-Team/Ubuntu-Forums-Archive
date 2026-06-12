---
title: "Quake 4 crash"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by CAUSTICROUTER on 2006-10-01
I found this bug wierd, when I try to play quake 4, the first level is loading, but it crashes back to the menu of the game.

---

### Post by billyfoxtrot on 2006-10-02
What are your system specs?  Did you try running quake4-smp as well as quake4?

---

### Post by CAUSTICROUTER on 2006-10-02
Intel Pentium 4 2.53Ghz
512MB Ram
Nvidia 6600GT
And yes I did try the quake4-smp.

---

### Post by Lord Illidan on 2006-10-02
The Quake 4 smp won't work unless you have a dual core processor...so it wouldn't have worked anyway.

I think it is more a problem with your .pk3 files..perhaps you need to copy them again and reinstall? Also, run it from a terminal, and see what it outputs.

---

### Post by CAUSTICROUTER on 2006-10-02
It doesn't even start anymore.

---

### Post by vayde on 2006-12-28
I'm having the same problem, but later in the game.

Inspiron 9300
2G cpu
1G ram
Nvidia Go6800

I'm using the drivers from the repository.  Figure this means I have to bang my head against the wall to install the latest?

---

### Post by Lord Illidan on 2006-12-28
I also had this problem now. And I solved it by enabling swap space. Apparently, u need a large amount of memory to run Q4...and in Edgy, swap space is disabled.

---

### Post by vayde on 2006-12-28
Im using Dapper.  As far as I know swap is active, though I certainly haven't had to use it yet.

Was this what you got from a terminal?:

idCollisionModelManagerLocal::TrmFromModel: model  not found.
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: rvClientMoveable '-1': cannot load collision model
********************
WARNING: idSession: triggering mainmenu watchdog
------------ Game Map Shutdown --------------

---

