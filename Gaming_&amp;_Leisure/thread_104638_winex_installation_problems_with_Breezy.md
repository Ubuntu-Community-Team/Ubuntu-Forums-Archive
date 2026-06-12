---
title: "winex installation problems with Breezy"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by blastradius on 2005-12-16
Hi

I'm trying to install winex in order to play Starcraft but there seems to be a compilation problem which i think may be caused by Breezy running GCC4.0 rather than 3.4.  
I have both installed but how do i get Ubuntu to compile with 3.4?

Thanks for any reply.

Here's the output.


Compiling ...




--------- Error log - file /home/eric/.WineCVS/sources/winex330/ErrorLog : ---------
make[1]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/unicode'
make[1]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/tools'
make[2]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/tools/winebuild'
make[2]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/tools/winedump'
make[2]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/tools/wmc'
make[2]: Entering directory `/home/eric/.WineCVS/sources/winex330/winex/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/eric/.WineCVS/sources/winex330/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by Perfect Storm on 2005-12-16
Before ./configure

```

CC=gcc-3.4
export CC

```

---

### Post by blastradius on 2005-12-16
[QUOTE=Artificial Intelligence]Before ./configure

```

CC=gcc-3.4
export CC

```[/QUOTE]


Thing is, i'm running the sh winex.sh and when i've picked a profile it just sets off doing its thing.  So i'm not actually doing a ./configure.
Thanks for your reply.

---

