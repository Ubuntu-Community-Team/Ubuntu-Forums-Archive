---
title: "CedegaCVS: Yet another problem"
date: 2006-01-21
forum: Gaming &amp; Leisure
---

### Post by Foucault on 2006-01-21
Hi!
Out of curiosity I've checked out the WineCVS.sh shell script to give it a shot. However I get the following error on make:

```
--------- Error log - file /home/foucault/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/wrc'
/usr/bin/gcc-3.4 -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -o wrc  dumpres.o genres.o newstruc.o preproc.o readres.o utils.o wrc.o writeres.o ppy.tab.o lex.ppl.o    y.tab.o lex.yy.o -L../../unicode -lwine_unicode -lfl
wrc.o: In function `main':
/home/foucault/.WineCVS/sources/cvscedega/winex/tools/wrc/wrc.c:559: undefined reference to `ppdebug'
lex.ppl.o: In function `push_buffer':
./ppl.l:1169: undefined reference to `ppdebug'
lex.ppl.o: In function `pplex':
./ppl.l:1259: undefined reference to `ppdebug'
collect2: ld returned 1 exit status
make[2]: *** [wrc] Error 1
make[2]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/foucault/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2

```

It's a common one, but none of the answers that I've found across the Internet helped a bit.
I've read somewhere that I should install flex-old instead of flex to avoid this error. I did that, cleaned the downloaded files, checked the CVS out again but I get the same error again and again. I have also tried to compile it with GCC 3.4 as some people state that this might help, however it didn't. I do not really mind if I won't get cedegaCVS to install; I just do not understand what causes this (apparently linker) error. Out of what I've read in various forums CedegaCVS has many many problems in compiling. :-k . Couldn't there be a precompiled one :rolleyes: ?

---

### Post by happyponcho42 on 2006-01-21
I guess I'm one of the lucky ones that got CedegaCVS to work.  It took quite a few attempts and I did give up for a few days, but I went back at it and it installed with no errors.  I ended up subscribing to it for a while.

Maybe you'll get lucky and the message just disappears :p.  It almost seems as though that's what happened with me.  Perhaps it was the result of me going apt-get package crazy the days in between my tries and eventually, the dependencies were satisfied.

---

