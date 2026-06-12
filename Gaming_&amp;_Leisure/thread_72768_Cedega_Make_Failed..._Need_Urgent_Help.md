---
title: "Cedega Make Failed... Need Urgent Help"
date: 2005-10-07
forum: Gaming &amp; Leisure
---

### Post by KrisDwyer on 2005-10-07
List of profiles (b to go back):

0 ) cvscedega_head
1 ) winex310
Enter choice:
0


Running Profile : cvscedega_head
/home/kris/.WineCVS/sources/cvscedega/wine












WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Compiling ...




--------- Error log - file /home/kris/.WineCVS/sources/cvscedega/ErrorLog : ---------
ts_xlib.c: In function `TSXOpenIM':
ts_xlib.c:1176: error: `XIM' undeclared (first use in this function)
ts_xlib.c:1176: error: syntax error before "r"
ts_xlib.c:1178: error: `r' undeclared (first use in this function)
ts_xlib.c:1178: warning: implicit declaration of function `XOpenIM'
ts_xlib.c:1178: error: `a0' undeclared (first use in this function)
ts_xlib.c:1178: error: `a1' undeclared (first use in this function)
ts_xlib.c:1178: error: `a2' undeclared (first use in this function)
ts_xlib.c:1178: error: `a3' undeclared (first use in this function)
ts_xlib.c: At top level:
ts_xlib.c:1183: error: syntax error before "TSXCheckIfEvent"
ts_xlib.c:1183: error: syntax error before '*' token
ts_xlib.c:1183: warning: type defaults to `int' in declaration of `TSXCheckIfEvent'
ts_xlib.c:1183: error: `TSXCheckIfEvent' declared as function returning a function
ts_xlib.c:1183: warning: type defaults to `int' in declaration of `XPointer'
ts_xlib.c:1183: error: syntax error before "a3"
ts_xlib.c:1186: warning: type defaults to `int' in declaration of `wine_tsx11_lock'
ts_xlib.c:1186: error: `wine_tsx11_lock' redeclared as different kind of symbol
../include/ts_xlib.h:19: error: previous declaration of `wine_tsx11_lock'
ts_xlib.c:1186: warning: data definition has no type or storage class
ts_xlib.c:1187: warning: type defaults to `int' in declaration of `r'
ts_xlib.c:1187: error: `r' used prior to declaration
ts_xlib.c:1187: warning: implicit declaration of function `XCheckIfEvent'
ts_xlib.c:1187: error: `a0' undeclared here (not in a function)
ts_xlib.c:1187: error: `a1' undeclared here (not in a function)
ts_xlib.c:1187: error: `a2' undeclared here (not in a function)
ts_xlib.c:1187: error: `a3' undeclared here (not in a function)
ts_xlib.c:1187: error: initializer element is not constant
ts_xlib.c:1187: warning: data definition has no type or storage class
ts_xlib.c:1188: warning: type defaults to `int' in declaration of `wine_tsx11_unlock'
ts_xlib.c:1188: error: `wine_tsx11_unlock' redeclared as different kind of symbol
../include/ts_xlib.h:20: error: previous declaration of `wine_tsx11_unlock'
ts_xlib.c:1188: warning: data definition has no type or storage class
ts_xlib.c:1189: error: syntax error before "return"
ts_xlib.c:1192: error: syntax error before '*' token
ts_xlib.c:1192: error: syntax error before '*' token
ts_xlib.c: In function `TSXSynchronize':
ts_xlib.c:1194: error: syntax error before '*' token
ts_xlib.c:1196: warning: implicit declaration of function `XSynchronize'
ts_xlib.c:1196: error: `a0' undeclared (first use in this function)
ts_xlib.c:1196: error: `a1' undeclared (first use in this function)
ts_xlib.c:1196: warning: assignment makes pointer from integer without a cast
ts_xlib.c: At top level:
ts_xlib.c:1201: error: syntax error before '*' token
ts_xlib.c:1203: error: syntax error before '*' token
ts_xlib.c: In function `TS_XInitImageFuncPtrs':
ts_xlib.c:1206: error: `a0' undeclared (first use in this function)
make[1]: *** [ts_xlib.o] Error 1
make[1]: Leaving directory `/home/kris/.WineCVS/sources/cvscedega/winex/tsx11'
make: *** [tsx11/libwine_tsx11.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

Please Help... as i need this done by tomorrow morning...

Thanks in advance,
Kris

---

### Post by KrisDwyer on 2005-10-07
oops wrong forum... this question is for 5.04

---

