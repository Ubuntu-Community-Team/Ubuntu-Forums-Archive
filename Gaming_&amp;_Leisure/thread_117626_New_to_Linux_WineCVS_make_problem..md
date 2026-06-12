---
title: "New to Linux WineCVS make problem."
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by racin on 2006-01-15
Here is the error log. It's being installed on a Gateway Laptop. I have worked through the wireless, sound, and midi problems. So this is next on my hit parade!
Thanks for the help in advance!
Error log - file /home/*****/.WineCVS/sources/winex310/ErrorLog : ---- -----
spec16.c:174: warning: pointer targets in assignment differ in signedness
spec16.c:180: warning: pointer targets in assignment differ in signedness
spec16.c:187: warning: pointer targets in assignment differ in signedness
spec16.c:191: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
spec16.c:201: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
spec16.c:202: warning: pointer targets in passing argument 1 of ‘strupper’ diffe r in signedness
spec16.c:211: warning: pointer targets in assignment differ in signedness
spec16.c:248: warning: pointer targets in assignment differ in signedness
spec16.c:271: warning: pointer targets in assignment differ in signedness
spec16.c:272: warning: pointer targets in passing argument 2 of ‘dump_bytes’ dif fer in signedness
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o spec32.o spec32.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o utils.o utils.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__int8=c har -D__int16=short -D__int32=int "-D__int64=long long" -o winebuild  import.o m ain.o parser.o relay.o res16.o res32.o spec16.o spec32.o utils.o      -L../../un icode -lwine_unicode
make[2]: Leaving directory `/home/*****/.WineCVS/sources/winex310/winex/tools/wi nebuild'
make[2]: Entering directory `/home/*****/.WineCVS/sources/winex310/winex/tools/w inedump'
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o debug.o debug.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o main.o main.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o misc.o misc.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o msmangle.o msmangle.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o output.o output.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o pe.o pe.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o search.o search.c
search.c: In function ‘symbol_from_prototype’:
search.c:189: warning: pointer targets in passing argument 3 of ‘str_match’ diff er in signedness
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o symbol.o symbol.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__int8=c har -D__int16=short -D__int32=int "-D__int64=long long" -o winedump  debug.o mai n.o misc.o msmangle.o output.o pe.o search.o symbol.o
make[2]: Leaving directory `/home/*****/.WineCVS/sources/winex310/winex/tools/wi nedump'
make[2]: Entering directory `/home/*****/.WineCVS/sources/winex310/winex/tools/w mc'
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o lang.o lang.c
bison -y  -d -t ./mcy.y
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o mcl.o mcl.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o utils.o utils.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o wmc.o wmc.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o write.o write.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o y.tab.o y.tab.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__int8=c har -D__int16=short -D__int32=int "-D__int64=long long" -o wmc  lang.o mcl.o uti ls.o wmc.o write.o     y.tab.o -L../../unicode -lwine_unicode -lfl
make[2]: Leaving directory `/home/*****/.WineCVS/sources/winex310/winex/tools/wm c'
make[2]: Entering directory `/home/*****/.WineCVS/sources/winex310/winex/tools/w rc'
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o dumpres.o dumpres.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o genres.o genres.c
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-b oundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "- D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/*****/.WineCVS/sources/winex310/winex/tools/wr c'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/*****/.WineCVS/sources/winex310/winex/tools'
make: *** [tools] Error 2

---

### Post by Mr_Grieves on 2006-01-15
Do you have to compile it yourself? Can't you just download it with apt-get/synaptic?

[https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

### Post by racin on 2006-01-15
I got this working using option # 3. Thanks for the help. I appreciate it!

---

