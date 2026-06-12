---
title: "Problems Compiling Graphical Crawl (Linley's Dungeon Crawl)"
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by NeSS Esqa on 2007-07-28
I'm trying to compile the graphical version of Linley's Dungeon Crawl. ([Graphical version]("http://crawlj.sourceforge.jp/down_e.html")) ([original website]("http://www.dungeoncrawl.org/"))

The instructions it gives is as follows:

> STEP1:  Get the original source
From the official site [http://www.dungeoncrawl.org/](http://www.dungeoncrawl.org/), download the source [ftp://ftp.dungeoncrawl.org/dev/4.0.x/src/dc400b26-src.tbz2](ftp://ftp.dungeoncrawl.org/dev/4.0.x/src/dc400b26-src.tbz2) and unpack the tarball.

% bunzip2 dc400b26-src.tbz2
% tar -xf dc400b26-src.tar
% cd dc400b26-src/source
 Edit the following line in AppHdr.h
    #define SAVE_DIR_PATH       "/opt/crawl/lib/"
     change it to "/home/foobar/crawl/lib/" etc.

  Fix the CR+LF code of mon-data.h
% nkf -d mon-data.h>tmp
% mv tmp mon-data.h

STEP2: Apply the patch
Download the patch from this page. The name will be "dc_e???_??????_src.zip" (??? is a version number) and unzip it. Copy the init.txt

% unzip dc_e???_??????_src.zip
% cp dc_e???_??????_src/init.txt ~/.crawlrc

Apply the patch and make:

% nkf -d -e ../dc_e???_??????_src/dc***.pat|patch
  (nkf -d converts CR+LF to CR  and nkf -e converts Japanese kanji code)
% make -f makefile.x11

If you are using MAC OSX, edit the makefile.x11 (guides are therein).
If you got an error like "Couldn't find Xlib.h", modify the INCLUDES line in makefile.x11 as follows:

INCLUDES = -I/usr/include/ncurses -I/usr/X11R6/include


Download the tile PNG files from here and unzip it into the SAVE_DIR_PATH you defined.
Congratulations! It is all.

You can change the fonts via the env variables. A sample script:

#! /bin/csh -f
setenv CRAWL_X11_FONT_CRT  "-alias-fixed-bold-r-normal--16-*"
setenv CRAWL_X11_FONT_STAT "-alias-fixed-bold-r-normal--16-*"
setenv CRAWL_X11_FONT_MSG "-alias-fixed-bold-r-normal--16-*"

./crawl

The problem is that when I try to make it, it gives me this:

libtile.h:2:22: error X11/Xlib.h: No such file or directory
libtile.h:3:19: error X11/X.h: No such file or directory
Make:*** [maps.o] Error 1

Then it spits me back out into the terminal.

I'm running 7.04 (Fiesty Fawn I think)

Any tips as to what I'm doing wrong and how to fix it?

I love Crawl, but I can't get used to the text interface.

---

### Post by DoktorSeven on 2007-07-28
When compiling, anytime you get a (something).h not found error, you need to install a development package for  whatever is missing.  Development packages are not installed by default; you'll have to search the packages for what looks similar, and the package must end in -dev.

Installing **apt-file** (sudo apt-get install apt-file) will help here; install it, run **sudo apt-file update**, then do **apt-file search X11/Xlib.h**:

```
$ apt-file search X11/Xlib.h
hugs: usr/lib/hugs/packages/X11/Graphics/X11/Xlib.hs
ivtools-dev: usr/include/IV-X11/Xlib.h
libghc6-x11-dev: usr/lib/X11-1.2/ghc-6.6/Graphics/X11/Xlib.hi
libx11-dev: usr/include/X11/Xlib.h
tendra: usr/lib/TenDRA/lib/include/x5/lib.api/X11/Xlib.h

```

The most likely candidate is one that is in /usr/include (the other one is IV-X11, not plain X11, so ignore it), so you need **libx11-dev**.  Similarly, a search for X11/X.h returns **x11proto-core-dev**, so those two are what you need.

---

### Post by NeSS Esqa on 2007-07-29
Thanks. It ran through cleanly, but now I can't figure out what command to run it.
Is there any local repository of terminal commands that work?
If not, how would I go about finding what the magic word is without resorting to trial and error?

Thanks for directing me to the specific packages as my Ubuntu machine does not currently have an internet connection (my next project).

---

### Post by DoktorSeven on 2007-07-29
from the instructions you posted, it should be 

./crawl 

from the directory you built it from.

---

### Post by NeSS Esqa on 2007-07-29
It says that that's a directory. I built it from my home directory.

---

### Post by Frem on 2007-07-29
I followed those instructions and got errors while trying to compile. 

Also, the patch didn't create Makefile.X11, I had to extract that from the patchfile myself. I think I missed something someplace.

```
g++ -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -O -DLINUX -O2 -fno-strength-reduce -c religion.cc 
g++ -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -O -DLINUX -O2 -fno-strength-reduce -c shopping.cc 
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
religion.cc:68: error: braces around scalar initializer for type &#8216;const char*&#8217;
g++ -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -O -DLINUX -O2 -fno-strength-reduce -c skills.cc 
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
make[1]: *** [religion.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: Leaving directory `/home/james/downloads/dc/dc400b26-src/source'
make: *** [all] Error 2

```

edit: also, the line "% nkf -d -e ../dc_e???_??????_src/dc***.pat|patch" doesn't work. That command will make it do a dry run, it just sits there. I had to use "nkf -d -e ../../patch/dc400b26j070.pat > patch" (yes, I renamed the "dc_e_whateverwhatever" folder "patch") and "patch -i patch"

---

### Post by NeSS Esqa on 2007-08-01
I think that renaming it may cause problems, but I'm not sure. I just deleted the "../" bit to get it where I am now.

---

### Post by Frem on 2007-08-02
Um, no... That's just the name of the directory. The source is a level down, in both of them. Besides, the first time I did it, I didn't rename and had the same problem.

Have you managed to get a binary out of this?

---

### Post by NeSS Esqa on 2007-08-02
Not yet. This is really disappointing. I was hoping to be able to get it to work. Maybe if I get Wine working, I could use the Windows binary...

---

### Post by Frem on 2007-08-02
Wine *does* run the Windows binary rather well. But it's wine, and it takes longer to start up and quit than a normal Linux binary would.

It would be really neat if we had the game in the Ubuntu repos, though.

edit: There's an enhanced graphical Windows version of the "Stone Soup" fork of the game that someone on the [Something Awful forum]("http://forums.somethingawful.com/showthread.php?threadid=2314850")s compiled for Windows. This *should* run in Wine, but I can't check right now. [link]("http://www.savefile.com/files/459821")

---

### Post by DKnight on 2007-08-09
I compiled it successfully. I've attached the binary (i386)  to this post (the SAVE_DIR_PATH is "/home/carlo/.crawl", sorry about that, and don't forget to put the PNGs there).

---

### Post by Frem on 2007-08-13
Sweet. Might I ask how you did it? ;-)

---

### Post by NeSS Esqa on 2007-09-01
It's nice to see progress on this. However, I cannot get this to run. The best result I get is:

"Segmentation Fault: Core Dumped"

Obviously this is not the intended result. Can you provide more information on how I am supposed to install/use this?

---

