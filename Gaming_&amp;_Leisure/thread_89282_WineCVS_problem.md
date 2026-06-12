---
title: "WineCVS problem"
date: 2005-11-12
forum: Gaming &amp; Leisure
---

### Post by klemens on 2005-11-12
I can't find the error can someone help me
make[2]: Entering directory `/home/klemens/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/klemens/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/klemens/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

This is what i get when i use the newest profile!
Pls help!

---

### Post by Uzari on 2005-11-12
The fix for that can be foudn here:
[http://ubuntuforums.org/showthread.php?t=76077](http://ubuntuforums.org/showthread.php?t=76077)

I personally still had problems after that, I completely deleted all traces of WineCVS after I found Wine in the package manager. Search Wine and you should find it, it automatically sets it up mostly, so it works after being installed(Im still trying to figure out CD's though)

---

