---
title: "cedega installation error"
date: 2005-12-28
forum: Gaming &amp; Leisure
---

### Post by Thunk on 2005-12-28
I tried installing CVScedega and got an error messegeduring the make stage. Refering to the troubleshotting chapter in the manual, I found this:

You need the XFree86-Mesa headers to compile Cedega with OpenGL support. It doesn't work with the nVidia OpenGL headers installed, install the Mesa headers instead.

How can I do it and is it safe to do it? Isn't it better to use the Nvidia headers in general?

Thanks!

EDIT:

I mismatched the solution to the error. The real error it gives me is:
```
make[2]: Entering directory `/home/tomer/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/tomer/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/tomer/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


```

Any ideas?

---

