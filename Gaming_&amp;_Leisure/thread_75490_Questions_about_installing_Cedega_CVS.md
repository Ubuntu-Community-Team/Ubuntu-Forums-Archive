---
title: "Questions about installing Cedega CVS"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by Goober on 2005-10-13
Hi Guys,

I am trying to install Cedega CVS, and not having much luck.  I am following the instructions [here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

I successfully typed this:

```
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```

into a Command Terminal, and everything installed just fine.  Now it wants me to go to the folder where WineCVS.sh is installed, and type in 

```
sh WineCVS.sh
```

That is all fine and dandy, but I can't find "WineCVS.sh".  I don't know where it installed to, and the search feature ain't helping.  Can somebody help?  Thanks in advance.

---

### Post by dafrabbit on 2005-10-13
You need to download the script form linuxgamers so type:

```
wget [http://cvscedega.linux-gamers.net/WineCVS.sh](http://cvscedega.linux-gamers.net/WineCVS.sh)
```

---

### Post by Goober on 2005-10-13
Ok, that worked, and I am currently installing.  Thanks a lot!

---

### Post by lokraan on 2005-10-18
did you succed in installing cedega ?

on a fresh breezy, updated, with
```
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
``` done

i get these : 

> 

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


    TIP: For a list of games working in WineX, go to this site:
    [http://www.transgaming.com/searchgame.php](http://www.transgaming.com/searchgame.php)
--------- Error log - file /home/gchauvel/.WineCVS/sources/cvscedega/ErrorLog : ---------
spec16.c:180: attention : pointer targets in assignment differ in signedness
spec16.c:186: attention : pointer targets in assignment differ in signedness
spec16.c:193: attention : pointer targets in assignment differ in signedness
spec16.c:197: attention : pointer targets in passing argument 1 of ‘strcpy’ diff er in signedness
spec16.c:207: attention : pointer targets in passing argument 1 of ‘strcpy’ diff er in signedness
spec16.c:208: attention : pointer targets in passing argument 1 of ‘strupper’ di ffer in signedness
spec16.c:217: attention : pointer targets in assignment differ in signedness
spec16.c:254: attention : pointer targets in assignment differ in signedness
spec16.c:277: attention : pointer targets in assignment differ in signedness
spec16.c:278: attention : pointer targets in passing argument 2 of ‘dump_bytes’ differ in signedness
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o spec32.o spec32.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o utils.o utils.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const= const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int6 4=long long" -o winebuild  import.o main.o parser.o relay.o res16.o res32.o spec 16.o spec32.o utils.o      -L../../unicode -lwine_unicode
make[2]: quittant le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/wine x/tools/winebuild »
make[2]: entrant dans le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/ winex/tools/winedump »
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o debug.o debug.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o main.o main.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o misc.o misc.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o msmangle.o msmangle.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o output.o output.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o pe.o pe.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o search.o search.c
search.c: In function ‘symbol_from_prototype’:
search.c:189: attention : pointer targets in passing argument 3 of ‘str_match’ d iffer in signedness
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o symbol.o symbol.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const= const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int6 4=long long" -o winedump  debug.o main.o misc.o msmangle.o output.o pe.o search. o symbol.o
make[2]: quittant le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/wine x/tools/winedump »
make[2]: entrant dans le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/ winex/tools/wmc »
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o lang.o lang.c
bison -y  -d -t ./mcy.y
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o mcl.o mcl.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o utils.o utils.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o wmc.o wmc.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o write.o write.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o y.tab.o y.tab.c
gcc -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const= const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int6 4=long long" -o wmc  lang.o mcl.o utils.o wmc.o write.o     y.tab.o -L../../unic ode -lwine_unicode -lfl
make[2]: quittant le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/wine x/tools/wmc »
make[2]: entrant dans le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/ winex/tools/wrc »
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o dumpres.o dumpres.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o genres.o genres.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-s tack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D_ _int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REE NTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: erreur: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: erreur: invalid lvalue in increment
make[2]: *** [newstruc.o] Erreur 1
make[2]: quittant le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/wine x/tools/wrc »
make[1]: *** [wrc] Erreur 2
make[1]: quittant le répertoire « /home/gchauvel/.WineCVS/sources/cvscedega/wine x/tools »
make: *** [tools] Erreur 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by Goober on 2005-10-18
No, I never got it working, and I've kinda given up on Cedega.  I am currently trying QEmu and WMware.

The Games that I want to play won't even work with Cedega.  They are mostly CivIV and the newer NFS games.

---

### Post by oblib on 2005-10-21
I had to get the older GCC
```

sudo apt-get install gcc-3.4
CC=gcc-3.4
export CC

```
I did that in the winex directory, and then did tools/wineinstall again and it worked (is working) after I got all of the Xlib libraries. I didn't use the script or that page you referred to above.
I don't know if it will work once it's done compiling, maybe I'll let you know.

Edit: it compiled, but once I got wine so it would execute (complained about missing a folder in my .wine directory) it would not run the .exe file. Probably more Xlib problems. Had the following error:```
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 45 requests (43 known processed) with 0 events remaining.

```

---

### Post by Xceptiona1 on 2006-12-02
I am getting hung up on the repositories section; the how-to says this...

Needed apps, packages, libraries:
wget, fontconfig, freetype2, freetype2-devel, bison, flex, libjpeg, libjpeg-devel, libpng, libpng-devel, zlib, zlib-devel, xorg-x11-devel (resp. XFree86-devel), Mesa (resp. xorg-x11-Mesa, XFree86-Mesa), Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel), freeglut, freeglut-devel

when it says resp. XFree86-devel and such, how do I get the repository information? I understand I need to add the repository to the sources.list file, but it doesnt say all the repo. info I need?

---

### Post by Forumdude on 2007-01-26
I am runnung Edgy and when I put in "sh WineCVS.sh" ($ sh WineCVS.sh won't work either) I get:
 
> test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

Help?](*,)

---

### Post by handy on 2007-01-28
In the last 15 months I am yet to hear anyone have a good thing to say about CVS Cedega!

I installed it on Breezy but couldn't do a thing with it!

Cedega runs GW, Eve-online & Far Cry great for me, but I don't like their pay for ever tactics, or some of the other things that Transgaming do...  

But I don't have to run windoze! :D

---

