---
title: "Problem with cvscedega"
date: 2005-04-22
forum: Gaming &amp; Leisure
---

### Post by Spode on 2005-04-22
When installing cvscedega with linuX-gamers winecvs.sh-script I get this during Make:
```
make[1]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT -I/usr/X11R6/include -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/christian/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
```After that the script stops. Any ideas?

I'm running Ubuntu 5.04 (Hoary Hedgehog)

---

### Post by jdodson on 2005-04-22
i work for a shop that makes software for printers(my department).  at times the developers put code into the CVS(like) system that breaks the entire build.  this seems to be the case.  delete all the cvs code you downloaded, wait a day and snag it again, hopefully it will be fixed then.  

thing is with getting cvs code it is buggier than the release, because usually the release has been tested more.  sometimes people dump chunks of untested code into cvs to meet deadlines or because they are lazy.  its kinda the downfall of going the cvs route at times.

unless.... they have a "stable" cvs codetree(which i have no idea if that is the case) then something else is wrong.

do you have the "build-essential" package installed?  fwiw.

---

