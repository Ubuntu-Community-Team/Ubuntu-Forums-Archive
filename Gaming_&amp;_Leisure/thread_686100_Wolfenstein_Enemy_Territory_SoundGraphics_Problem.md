---
title: "Wolfenstein: Enemy Territory Sound/Graphics Problem"
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by ondo311 on 2008-02-02
When i start the game in console i get this in teh sound part of the script:

```
------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/matthew/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/matthew/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/matthew/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae85fbb4  
Sys_LoadDll(ui) succeeded!

```

No sound goes through ... what do i do?!!

And as for the graphics problem, whenever I leave the game it has the graphix really off, there set for the normal 1440x900, but its zoomed in and it looks as if it is 1024x760   is there a way to fix this also?


Thanks for your help

---

### Post by ondo311 on 2008-02-02
when i type in
```
killall esd
```

i get
```
esd: no process killed
```

---

