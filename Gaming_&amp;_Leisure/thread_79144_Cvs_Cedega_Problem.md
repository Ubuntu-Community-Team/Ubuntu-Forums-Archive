---
title: "Cvs Cedega Problem"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by orgy on 2005-10-19
i tried installing cvscedega from WineCVS.sh and i get this error:

gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: En la funci&#243;n &#8216;handle_ani_list&#8217;:
newstruc.c:740: error: l-valor inv&#225;lido en incremento
newstruc.c: En la funci&#243;n &#8216;new_ani_curico&#8217;:
newstruc.c:851: error: l-valor inv&#225;lido en incremento
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2

those are the last 13 lines.

im on a toshiba tecra, centrino 1.6, 512 ram, gforce fx go 5200 64 mb,

---

### Post by Mustard on 2005-10-19
Which profile did you choose when you ran WineCVS.sh?  Did you try the 'bleeding edge' ones or the 'regular' one?  I think the one that I compiled succesfully was the third option (rembering they are numbered starting with '0', so the third option is keypress '2').

---

### Post by glaze on 2005-10-20
If you're using Ubuntu Breezy, then try to reinstall cvscedega with command:
**CC='gcc-3.3' sh WineCVS.sh**
That's because the code does not compile with Breezy's gcc 4.0.1.

---

### Post by Donza on 2005-10-20
I have the same problem. When compiling it gives following error:
```
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/donza/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/donza/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

I have followed these instructions: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45")

---

### Post by Mustard on 2005-10-20
which profile did you try to compile, Donza?

---

### Post by oblib on 2005-10-21
Similar to what glaze says above, I had to get the older GCC
```

sudo apt-get install gcc-3.4
CC=gcc-3.4
export CC

```
I did that in the winex directory, and then did tools/wineinstall again and it worked (is working) after I got all of the Xlib libraries

Edit: it compiled, but once I got wine so it would execute (complained about missing a folder in my .wine directory) it would not run the .exe file. Probably more Xlib problems. Had the following error:```
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 45 requests (43 known processed) with 0 events remaining.

```

---

### Post by KiLLeR_WoMBaT on 2005-11-27
I'm having the same problem as you guys.  Has anyone found the cure?

---

### Post by blastradius on 2005-12-06
Smae problem for me.  Using Breezy, get to make and same errors.  
I have gcc3.4 and 4.0 installed, how do i get cedega to use 3.4 to compile itself, i run the script sh WineCVS.sh, pick a profile and off it goes.
How do i get it to use 3.4, if i uninstall 4.0 i lose loads of stuff.

Yes i'm a newbie!!

Thanks in advance.  I just want Starcraft to run.

---

