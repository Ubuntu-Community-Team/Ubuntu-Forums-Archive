---
title: "wine/cegegaCVS won't compile after checkout/config stage"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by voiceofxile on 2006-07-07
Has anyone using a 64 bit processor had problems compiling cvscedega/wine?
Can someone suggest a way for me to correct this error? Thank you for your time and help. 
```

Compiling ...




--------- Error log - file /home/"USER"/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/xile/.WineCVS/sources/cvscedega/winex/unicode'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o casemap.o casemap.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:153:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1035:2: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1038: error: syntax error before '*' token
../include/winnt.h:1038: warning: type defaults to `int' in declaration of `PCONTEXT'
../include/winnt.h:1038: warning: data definition has no type or storage class
../include/winnt.h:2073: error: syntax error before "PCONTEXT"
../include/winnt.h:2073: warning: no semicolon at end of struct or union
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `EXCEPTION_POINTERS'
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `PEXCEPTION_POINTERS'
../include/winnt.h:2074: warning: data definition has no type or storage class
../include/winnt.h:2086: error: syntax error before "PCONTEXT"
../include/winnt.h:2098: error: syntax error before "ExceptionInfo"
../include/winnt.h:2101: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declaration of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or storage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POINTERS"
../include/winbase.h:123: warning: type defaults to `int' in declaration of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or storage class
../include/winbase.h:1366: error: syntax error before "CONTEXT"
../include/winbase.h:1503: warning: type defaults to `int' in declaration of `CONTEXT'
../include/winbase.h:1503: error: syntax error before '*' token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/xile/.WineCVS/sources/cvscedega/winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Fri Jul  7 13:49:44 EDT 2006
Installation Done
======================
Type as User: cvscedega

```

---

### Post by vem0m on 2006-07-07
u try whats in [THIS LINK?]("http://www.ubuntuforums.org/showthread.php?t=193814")

---

### Post by voiceofxile on 2006-07-07
Yes I have tried that link, and I had success up to the compilation stage, which is after the selecting the profile, CVS checkout, etc. 
Any suggestions as to what options I can use with  "make" to enable it to recognize my CPU type?

---

### Post by vem0m on 2006-07-07
i use the acuall cedega so i am not sure but from the error it is wanting u to tell it a CPU type might be a perameter there u need to add not sure tho

---

### Post by voiceofxile on 2006-07-09
how do I add a CPU parameter?

---

