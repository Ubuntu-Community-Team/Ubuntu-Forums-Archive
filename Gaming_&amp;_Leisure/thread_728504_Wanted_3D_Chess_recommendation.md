---
title: "Wanted: 3D Chess recommendation"
date: 2008-03-18
forum: Gaming &amp; Leisure
---

### Post by Samurai Penguin on 2008-03-18
I would like a 3D Chess recommendation, one that's Free and has
the best 3D graphics quality.

Also, I just went off-siite to Portal and it says it will be released in the fall
of 2007. We're well past that time. Has it been tossed or still in the works?

---

### Post by compiledkernel on 2008-03-18
DreamChess I believe fits that bill. 

[http://www.dreamchess.org/](http://www.dreamchess.org/)

---

### Post by Samurai Penguin on 2008-03-19
I Downloaded the package and ran ,/configure and received the following error:

error: Cannot find Mini-XML header file

here's the Terminal printout:

root@HAL:/home/tomana# cd Desktop
root@HAL:/home/tomana/Desktop# cd dreamchess-0.2.0
root@HAL:/home/tomana/Desktop/dreamchess-0.2.0# ./config
bash: ./config: No such file or directory
root@HAL:/home/tomana/Desktop/dreamchess-0.2.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for bison... no
checking for inline... inline
checking for ISO C99 varargs macros... yes
checking for GNU C varargs macros... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.6... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking for SDL_image.h... no
checking for SDL_opengl.h... no
checking for sqrt in -lm... yes
checking for compress in -lz... no
checking for png_create_read_struct in -lpng... no
checking for jpeg_CreateCompress in -ljpeg... no
checking for IMG_LoadPNG_RW in -lSDL_image... no
checking for glBegin in -lGL... no
checking for SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mxml.h usability... no
checking mxml.h presence... no
checking for mxml.h... no
configure: error: Cannot find Mini-XML header file.
root@HAL:/home/tomana/Desktop/dreamchess-0.2.0# 

any install help is appreciated

---

### Post by compiledkernel on 2008-03-19
[http://getdeb.net/app/DreamChess](http://getdeb.net/app/DreamChess)

They provide a Gutsy package.

---

### Post by Perfect Storm on 2008-03-19
> checking for flex... no
checking for bison... no
checking for SDL - version >= 1.2.6... no
checking for SDL_image.h... no
checking for SDL_mixer.h... no
checking mxml.h usability... no

sudo aptitude instal flex bison libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libmxml-dev

---

### Post by Cresho on 2008-03-19
too funny!  open add and remove program in your start.  select "all open source applications."  do a search for dream and click and apply and it is installed.  no need to do some reconfiguring....but good learning experience if you install from terminal.  GO the easy route if you get frustrated.


HEY WAIT A MINUTE!  its updated.  the add and remove has an older version....hmmm.  This new one has way better graphics.  I tried the one with the deb files.  It installed just fine.  I installed the data and then the dreamchess.

In trying the terminal way, sudo aptitude instal flex bison libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libmxml-dev    the terminal says "This aptitude does not have Super Cow Powers."  BTW, I am running hardy heron.
"

---

### Post by DoktorSeven on 2008-03-19
You're missing a final "L" in "install" on "the terminal way". 

```
sudo aptitude install flex bison libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libmxml-dev
```

---

### Post by Perfect Storm on 2008-03-19
aye, a mis-type instal should be install

---

### Post by sub2007 on 2008-03-19
Also, you could try Brutal Chess. Lovely 3D graphics, very hard AI. should be availible in Synaptic ;)

---

### Post by compiledkernel on 2008-03-19
Brutal Chess's AI is about as forgiving, as AI is on my Ubuntu Gamers Arena changes. 

:lolflag:

---

### Post by Cresho on 2008-03-19
yeah, I tried the line and that one works but it complains of  missing mini-xml.  So I went to the site and downloaded mxml-2.5.tar.gz and installed that one.  Still complains.  Now Im wondering if I should install an older one.

I wonder if the guy trying it installed it.

In anycase, I am on hardy heron.  It has libmxml1 and libmxml-dev installed by default and contains info of mini-xml.  Now I am wondering if this is a bug?  I am still in beta.

---

### Post by Perfect Storm on 2008-03-19
Lewt me give it a go....I'll report back later

---

### Post by Perfect Storm on 2008-03-19
> **compiledkernel said:**
> Brutal Chess's AI is about as forgiving, as AI is on my Ubuntu Gamers Arena changes. 

:lolflag:

with ironfist...muwhahaha! :KS

---

### Post by Perfect Storm on 2008-03-19
ok save the source to your Desktop.

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install bison flex libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libmxml-dev libgl1-mesa-dev libglu1-mesa-dev


cd ~/Desktop
tar zxfv dreamchess-0.2.0.tar.gz
cd dreamchess-0.2.0
./configure
make
sudo checkinstall
cd && dreamchess
```


tested on Ubuntu 7.10 64-bit Gnome

---

### Post by Cresho on 2008-03-19
yeah, its strange, still cannot fine mini-xml.

dont crack your head on my alpha hardy heron.  Its already installed with the deb files but I am wondering wny mini-xml is not in my shizzel.

---

### Post by Perfect Storm on 2008-03-19
I think you should report it to the Ubuntu devs - to make sure they know.

---

