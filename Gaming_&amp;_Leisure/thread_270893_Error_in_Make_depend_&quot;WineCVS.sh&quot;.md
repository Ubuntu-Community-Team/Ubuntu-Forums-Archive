---
title: "Error in Make depend &quot;WineCVS.sh&quot;"
date: 2006-10-03
forum: Gaming &amp; Leisure
---

### Post by maxjivi05 on 2006-10-03
> flex -Cf  -d -8 ./parser.l
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/lib/dx9wine/include/wine\""  -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2  -o lex.yy.o lex.yy.c
lex.yy.c:9174: error: syntax error before numeric constant
lex.yy.c: In function `yy_scan_string':
lex.yy.c:9175: error: number of arguments doesn't match prototype
lex.yy.c:367: error: prototype declaration
lex.yy.c:9177: warning: passing arg 1 of `strlen' makes pointer from integer without a cast
lex.yy.c:9177: warning: passing arg 1 of `yy_scan_bytes' makes pointer from integer without a cast
./parser.l: At top level:
lex.yy.c:8687: warning: `yyunput' defined but not used
lex.yy.c:9266: warning: `yy_top_state' defined but not used
make[2]: *** [lex.yy.o] Error 1
make[2]: Leaving directory `/home/max/.WineCVS/sources/dx9wine/wine/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/max/.WineCVS/sources/dx9wine/wine/tools'
make: *** [tools] Error 2


Error in Make depend

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

I thought it was that I didn't have Make installed but I checked and I have no clue what to do anyone please care to help?

---

