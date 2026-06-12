---
title: "Cedega CVS install oops"
date: 2005-03-22
forum: Gaming &amp; Leisure
---

### Post by wbeck85 on 2005-03-22
I found this site to install Cedega CVS easily. It is [here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)


However, i ran into the following problem after selecting the option #0. It ran through its setup and got as far as make. Then the error occured.

--------- Error log - file /home/wbeck85/.WineCVS/sources/cvscedega/E rrorLog : ---------
make[1]: Entering directory `/home/wbeck85/.WineCVS/sources/cvscedega /winex/unicode'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-kee p-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D __int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D _REENTRANT -I/usr/X11R6/include -o casemap.o casemap.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:148:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1030:2: #error You need to define a CONTEXT for yo ur CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1033: error: syntax error before '*' token
../include/winnt.h:1033: warning: type defaults to `int' in declarati on of `PCONTEXT'
../include/winnt.h:1033: warning: data definition has no type or stor age class
../include/winnt.h:2068: error: syntax error before "PCONTEXT"
../include/winnt.h:2068: warning: no semicolon at end of struct or un ion
../include/winnt.h:2069: warning: type defaults to `int' in declarati on of `EXCEPTION_POINTERS'
../include/winnt.h:2069: warning: type defaults to `int' in declarati on of `PEXCEPTION_POINTERS'
../include/winnt.h:2069: warning: data definition has no type or stor age class
../include/winnt.h:2081: error: syntax error before "PCONTEXT"
../include/winnt.h:2093: error: syntax error before "ExceptionInfo"
../include/winnt.h:2096: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declarat ion of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or sto rage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POI NTERS"
../include/winbase.h:123: warning: type defaults to `int' in declarat ion of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or sto rage class
../include/winbase.h:1362: error: syntax error before "CONTEXT"
../include/winbase.h:1499: warning: type defaults to `int' in declara tion of `CONTEXT'
../include/winbase.h:1499: error: syntax error before '*' token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/wbeck85/.WineCVS/sources/cvscedega/ winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Anyone make anythign of it? is it because of my x86_64 archetecture?

---

### Post by Beire on 2005-03-22
yeh i don't get that cvs either. It installed for me but the cvscedega command just doesn't work  :(

---

### Post by Lodes on 2005-03-22
the cvscedega executable is in your ~/bin directory, just put it in your usr/local/bin directory or /usr/bin whatever.

---

### Post by wbeck85 on 2005-03-22
[QUOTE=wbeck85]I found this site to install Cedega CVS easily. It is [here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)


However, i ran into the following problem after selecting the option #0. It ran through its setup and got as far as make. Then the error occured.

--------- Error log - file /home/wbeck85/.WineCVS/sources/cvscedega/E rrorLog : ---------
make[1]: Entering directory `/home/wbeck85/.WineCVS/sources/cvscedega /winex/unicode'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-kee p-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D __int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D _REENTRANT -I/usr/X11R6/include -o casemap.o casemap.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:148:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1030:2: #error You need to define a CONTEXT for yo ur CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1033: error: syntax error before '*' token
../include/winnt.h:1033: warning: type defaults to `int' in declarati on of `PCONTEXT'
../include/winnt.h:1033: warning: data definition has no type or stor age class
../include/winnt.h:2068: error: syntax error before "PCONTEXT"
../include/winnt.h:2068: warning: no semicolon at end of struct or un ion
../include/winnt.h:2069: warning: type defaults to `int' in declarati on of `EXCEPTION_POINTERS'
../include/winnt.h:2069: warning: type defaults to `int' in declarati on of `PEXCEPTION_POINTERS'
../include/winnt.h:2069: warning: data definition has no type or stor age class
../include/winnt.h:2081: error: syntax error before "PCONTEXT"
../include/winnt.h:2093: error: syntax error before "ExceptionInfo"
../include/winnt.h:2096: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declarat ion of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or sto rage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POI NTERS"
../include/winbase.h:123: warning: type defaults to `int' in declarat ion of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or sto rage class
../include/winbase.h:1362: error: syntax error before "CONTEXT"
../include/winbase.h:1499: warning: type defaults to `int' in declara tion of `CONTEXT'
../include/winbase.h:1499: error: syntax error before '*' token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/wbeck85/.WineCVS/sources/cvscedega/ winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Anyone make anythign of it? is it because of my x86_64 archetecture?[/QUOTE]
 Well, the problem was solved with a fresh install of ubuntu hoary of the i386 flavor. Now it works :)

---

### Post by bored2k on 2005-03-22
My problem was solved by installing cedega 4.2.1 ^_^ .

---

### Post by wbeck85 on 2005-03-23
[QUOTE=bored2k]My problem was solved by installing cedega 4.2.1 ^_^ .[/QUOTE]
 but that isnt free, is it?

---

### Post by foxy123 on 2005-05-21
[QUOTE=Lodes]the cvscedega executable is in your ~/bin directory, just put it in your usr/local/bin directory or /usr/bin whatever.[/QUOTE]

in this case I've got the following:
```
bash: /usr/bin/cvscedega: Permission denied
``` 
I guess all programmes in /usr/bin should be executed with sudo or under root.

---

### Post by fackamato on 2005-05-21
[QUOTE=foxy123]in this case I've got the following:
```
bash: /usr/bin/cvscedega: Permission denied
``` 
I guess all programmes in /usr/bin should be executed with sudo or under root.[/QUOTE]

err, no. to run an app as sudo/root whcih doesn't require it is like sticking a shotgun in your mouth and playing with the trigger. check if you got executable permissions on the filesystem.

---

### Post by foxy123 on 2005-05-21
[QUOTE=fackamato]err, no. to run an app as sudo/root whcih doesn't require it is like sticking a shotgun in your mouth and playing with the trigger. check if you got executable permissions on the filesystem.[/QUOTE]
no, I am not going to run it as a root. The thing is that when I installed cedega from cvs, it put cvscedega file in ~./WineCVS/installs/cvscedega/bin/WineCSSFunctions. So I have copied it in /usr/bin.

ok, I have chmoded the file but it does not run at all. Has anyone was successful in installing cvscedega on Ubuntu?

---

