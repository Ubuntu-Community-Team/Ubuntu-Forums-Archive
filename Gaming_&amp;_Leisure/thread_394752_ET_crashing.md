---
title: "ET crashing"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by Weaseal on 2007-03-27
Ok, so I posted before with a problem regarding ET crashing, but now I have pinned down (what I believe is) the error:

[b]"Sys_LoadDll(/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so)...
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so) failed:
"/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so: cannot map zero-fill pages: Cannot allocate memory"
Sys_LoadDll(qagame) failed dlopen() completely![/b]

----- CL_Shutdown -----

RE_Shutdown( 1 )

-----------------------
----- Server Shutdown -----
---------------------------
----- CL_Shutdown -----
-----------------------

Sys_Error: VM_Create on game failed "

Why would it have trouble allocating the memory?   The game runs fine on the same comp in Windows.

---

### Post by Iarwain ben-adar on 2007-03-27
Hi there,

i am not an expert in this, but could it be that you have too little memory? (swap not activated or such?)


Iarwain

---

### Post by Weaseal on 2007-03-28
Yes, in fact!  The swap was not activated.  Actually, it was not activated because it was corrupt.  You'd think the system would have tried harder to inform me of this?  Anyway, it's fixed now, thanks!

I just wiped and recreated the swap partition.

---

### Post by Iarwain ben-adar on 2007-03-28
Good you got it fixed :D


Iarwain

---

