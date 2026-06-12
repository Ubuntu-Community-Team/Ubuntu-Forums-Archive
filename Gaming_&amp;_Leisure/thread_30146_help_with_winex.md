---
title: "help with winex"
date: 2005-04-27
forum: Gaming &amp; Leisure
---

### Post by wasynyt on 2005-04-27
make[1]: Entering directory `/home/timo/omat/ohjelmat/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/timo/omat/ohjelmat/winex/unicode'
make[1]: Entering directory `/home/timo/omat/ohjelmat/winex/tools'
make[2]: Entering directory `/home/timo/omat/ohjelmat/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/timo/omat/ohjelmat/winex/tools/winebuild'
make[2]: Entering directory `/home/timo/omat/ohjelmat/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/timo/omat/ohjelmat/winex/tools/winedump'
make[2]: Entering directory `/home/timo/omat/ohjelmat/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/timo/omat/ohjelmat/winex/tools/wmc'
make[2]: Entering directory `/home/timo/omat/ohjelmat/winex/tools/wrc'
cc -g -O2 -Wall -D__const=const -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -o wrc  dumpres.o genres.o newstruc.o preproc.o readres.o utils.o wrc.o writeres.o ppy.tab.o lex.ppl.o    y.tab.o lex.yy.o -L../../unicode -lwine_unicode -lfl
wrc.o(.text+0xb1f): In function `main':
/home/timo/omat/ohjelmat/winex/tools/wrc/wrc.c:632: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
wrc.o(.text+0x92b):/home/timo/omat/ohjelmat/winex/tools/wrc/wrc.c:560: undefined reference to `ppdebug'
lex.ppl.o(.text+0x3aa9): In function `push_buffer':
/home/timo/omat/ohjelmat/winex/tools/wrc/./ppl.l:1059: undefined reference to `ppdebug'
lex.ppl.o(.text+0x3ddc): In function `pop_buffer':
/home/timo/omat/ohjelmat/winex/tools/wrc/./ppl.l:1149: undefined reference to `ppdebug'
make[2]: *** [wrc] Error 1
make[2]: Leaving directory `/home/timo/omat/ohjelmat/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/timo/omat/ohjelmat/winex/tools'
make: *** [tools] Error 2

Compilation failed, aborting install.

so thats the problem, it gives me an strage error and aborts...
if you want to see more of that just ask...
im trying to install it thru cvs source
i will appreciate if you could answere quickly..

ps.if this is the wrong places just put it where it belongs

---

### Post by bored2k on 2005-04-27
It's not the solution, but WineX is old. It is now called Cedega. You can build a free CVS following instructions on:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

---

### Post by wasynyt on 2005-04-27
tryied that script..
runned sh WineCVS.sh at first.. then found help..
-> runned sh WineCVS.sh refresh which encountered an error at make stage...

e of `tmpnam' is dangerous, better use `mkstemp'
wrc.o(.text+0x92b):/home/timo/.WineCVS/sources/cvscedega/winex/tools/wrc/wrc.c:560: undefined reference to `ppdebug'
lex.ppl.o(.text+0x3aa9): In function `push_buffer':
/home/timo/.WineCVS/sources/cvscedega/winex/tools/wrc/./ppl.l:1169: undefined reference to `ppdebug'
lex.ppl.o(.text+0x3ddc): In function `pop_buffer':
/home/timo/.WineCVS/sources/cvscedega/winex/tools/wrc/./ppl.l:1259: undefined reference to `ppdebug'
make[2]: *** [wrc] Error 1
make[2]: Leaving directory `/home/timo/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/timo/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

what next... im confused as this seems to be the same error i got before
 ](*,)

---

### Post by wasynyt on 2005-04-29
now i got it installed.
thanks for that link (all taht it required was an fresh installation of system)
now goingto try installing some games
 =D>   :)

---

