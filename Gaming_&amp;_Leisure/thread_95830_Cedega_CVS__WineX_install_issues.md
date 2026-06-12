---
title: "Cedega CVS / WineX install issues"
date: 2005-11-27
forum: Gaming &amp; Leisure
---

### Post by KiLLeR_WoMBaT on 2005-11-27
I have followed the instructions several times to the letter.  Here is what I end up with EVERY time I try to either run WineCVS.sh or manually compile Winex:

newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/daniel/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/daniel/winex/tools'
make: *** [tools] Error 2

Nothing fixes this.  Also, when running $sh WineCVS.sh and trying to choose a profile; which one do you choose for Breezy Badger?  I have tried them all and they all error out.

-WoMBaT

---

