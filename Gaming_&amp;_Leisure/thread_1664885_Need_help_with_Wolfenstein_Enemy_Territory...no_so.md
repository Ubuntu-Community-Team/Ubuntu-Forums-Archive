---
title: "Need help with Wolfenstein: Enemy Territory...no sound"
date: 2011-01-11
forum: Gaming &amp; Leisure
---

### Post by ImageJPEG on 2011-01-11
I've tried just about everything I can do. I've tried following this guide: _[http://www.hirntot.org/distribution/viewtopic.php?f=15&t=1074](http://www.hirntot.org/distribution/viewtopic.php?f=15&t=1074)_ with no luck.

I get the same exact error as the person in the first post. I've followed all the websites that they link to and I still come up with this error:

> ----- finished R_Init -----
Sys_LoadDll(/home/josh/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/josh/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/josh/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xecd46f40  
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
[et-sdl-sound] info   : doneIt would be quite awesome if I could get some help with this issue. It's giving me a headache...also, I have set my sound quality on ultra high by the way.

---

### Post by garyhibdon on 2011-01-11
First, i'd try to turn the sound quality down to a standard setting. if that doesnt work, then maybe you can uninstall and try again. if you have all of the drivers installed now for your sound, maybe it can make the link to the correct directories. Other then that you may, try 

```
 sudo apt-get install alsa
```

---

