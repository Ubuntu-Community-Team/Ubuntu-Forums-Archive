---
title: "CEDEGA - Error in Make"
date: 2006-11-24
forum: Gaming &amp; Leisure
---

### Post by Re DeL SiLeNziO on 2006-11-24
Hi, I'm a new forum member.. I have this problem with Cedega make in the Cedega script:

```
make[1]: Entering directory `/home/carmine/.WineCVS/sources/cvscedega/winex/libs/wpp'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/carmine/.WineCVS/sources/cvscedega/winex/libs/wpp'
make[1]: Entering directory `/home/carmine/.WineCVS/sources/cvscedega/winex/port'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/carmine/.WineCVS/sources/cvscedega/winex/port'
make[1]: Entering directory `/home/carmine/.WineCVS/sources/cvscedega/winex/unicode'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,- -execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o casemap.o casema p.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:153:3: error: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1035:2: error: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1038: error: syntax error before ‘*’ token
../include/winnt.h:1038: warning: type defaults to ‘int’ in declaration of ‘PCONTEXT’
../include/winnt.h:1038: warning: data definition has no type or storage class
../include/winnt.h:2090: error: syntax error before ‘PCONTEXT’
../include/winnt.h:2090: warning: no semicolon at end of struct or union
../include/winnt.h:2091: warning: type defaults to ‘int’ in declaration of ‘EXCEPTION_POINTERS’
../include/winnt.h:2091: warning: type defaults to ‘int’ in declaration of ‘PEXCEPTION_POINTERS’
../include/winnt.h:2091: warning: data definition has no type or storage class
../include/winnt.h:2103: error: syntax error before ‘PCONTEXT’
../include/winnt.h:2115: error: syntax error before ‘ExceptionInfo’
../include/winnt.h:2118: error: syntax error before ‘epointers’
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before ‘LPCONTEXT’
../include/winbase.h:121: warning: type defaults to ‘int’ in declaration of ‘LPCONTEXT’
../include/winbase.h:121: warning: data definition has no type or storage class
../include/winbase.h:123: error: syntax error before ‘LPEXCEPTION_POINTERS’
../include/winbase.h:123: warning: type defaults to ‘int’ in declaration of ‘LPEXCEPTION_POINTERS’
../include/winbase.h:123: warning: data definition has no type or storage class
../include/winbase.h:1370: error: syntax error before ‘CONTEXT’
../include/winbase.h:1510: warning: type defaults to ‘int’ in declaration of ‘CONTEXT’
../include/winbase.h:1510: error: syntax error before ‘*’ token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/carmine/.WineCVS/sources/cvscedega/winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

I have tried to run script again, but I always run it wothout parameters!!

Thanks for helps and excuse me for my bad english!!!! ](*,) 

Re DeL SiLenZiO

---

### Post by Re DeL SiLeNziO on 2006-11-29
Nothing?? :(  ](*,)

---

### Post by kingpombär on 2007-03-11
Did you already fix the problem? 


I found a French Site dealing with it but I don't understand anything^^ 

[http://forum.ubuntu-fr.org/viewtopic.php?pid=716488](http://forum.ubuntu-fr.org/viewtopic.php?pid=716488)

It says something about gcc

```

$ sudo apt-get install gcc-3.4
$ export CC=gcc-3.4 make
```

Is it possible to install an older version of gcc without problems? Mine is 4.1.2.
When I tried to do this some time ago on my HTPC I damaged something. I'm new to Linux and don't want to kill my system (again^^). 

Do you use the i686 version of Ubuntu? 

I do. And I have the same error....





sorry for my English ](*,)

---

### Post by bastiegast on 2007-03-11
AFAIK Ubuntu doesn't have an i686 version anymore. 
Anyway you better stay as far away as you can from cvscedega, it's only gonna give you trouble, better try wine as might play some game's better than cedega lately.

---

### Post by handy on 2007-03-11
I agree, cvscedega is a pain!

[Here is a how-to link for cvscedega, by someone who knows how to make it work.]("http://ubuntuforums.org/showthread.php?t=193814&highlight=cvscedega")

Good luck!

---

### Post by kingpombär on 2007-03-12
Thanks for the link! .. I tried it but I got the same error again

```
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make
```


I think it has something to do with the issue that wine doesn't run un 64 Bit OS. When I try to install libwine with the Synaptic Package Manager I get the following error

```
libwine:
 Hängt ab: wine  but it is not installable
```

Hängt ab = depends on

---

