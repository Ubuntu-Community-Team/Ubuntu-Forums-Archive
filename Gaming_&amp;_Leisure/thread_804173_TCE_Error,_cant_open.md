---
title: "TC:E Error, cant open"
date: 2008-05-22
forum: Gaming &amp; Leisure
---

### Post by NR1224 on 2008-05-22
I love ET: Wolfenstein, so i downloaded and installed this mod according to the directions [http://gaming.gwos.org/doku.php/guides:32bit:tce#truecombat_elite](http://gaming.gwos.org/doku.php/guides:32bit:tce#truecombat_elite). When i try to run TC:E though, i get this, 

Sys_LoadDll(/home/nathan/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/nathan/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so) failed:
"libstdc++.so.5: cannot open shared object file: No such file or directory"
Sys_LoadDll(ui) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on UI failed
Shutdown tty console
:confused:

Any suggestions?
Thanks!

---

### Post by Perfect Storm on 2008-05-23
Check if **libstdc++5** is installed.

---

### Post by flytripper on 2008-06-26
A>I's post worked fer me :) thanks

---

