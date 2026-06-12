---
title: "ta3d install"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by spartan777 on 2007-05-27
I've installed allegro 4.2 through synaptic, and fmod was installed manually. When i try to install ta3d, i still get an error telling my allegro wasn't installed correctly;

```
calvin@calvin-desktop:~$ cd /home/calvin/Desktop/ta3d
calvin@calvin-desktop:~/Desktop/ta3d$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lz... yes
checking for main in -lfmodex... yes
checking for allegro-config... /usr/bin/allegro-config
checking for Allegro - version >= 4.2.0... no
*** Could not run Allegro test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means Allegro was incorrectly installed
*** or that you have moved Allegro since it was installed. In the latter case, you
*** may want to edit the allegro-config script: /usr/bin/allegro-config
configure: error: TA3D requires Allegro >= 4.2.0 to be installed
calvin@calvin-desktop:~/Desktop/ta3d$ 



```

---

### Post by yabbadabbadont on 2007-05-27
Make sure that you have installed liballegro4.2-dev

---

### Post by spartan777 on 2007-05-28
i do have liballegro4.2-dev installed.

---

### Post by perky on 2007-07-27
Has anyone had any luck figuring this out?  I am getting the exact same problem :\

---

### Post by perky on 2007-07-27
Managed to get ./configure to work.

First, in a console you need to type:

```

sudo ln -s /usr/local/lib/allegro /lib/allegro

```

I ran into another error in the ./configure which said AllegroGL was missing.

Dowload AllegroGL (search google), extract to a directory, cd to it, then:
```

./configure
make
sudo make install

```

This should install AllegroGL and allow ./configure (of TA3D) to run successfully.


I have run into yet ANOTHER error while running 'make' (after a successful ./configure )
```

g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
main.cpp: In function ‘void install_TA_files(String)’:
main.cpp:436: error: ‘file_size_ex’ was not declared in this scope
make[2]: *** [main.o] Error 1

```

After a brief look at the main.cpp source, it seems that the line 436:
```

int limit = file_size_ex( ( path_to_TA_cd + "totala2.hpi" ).c_str() ); )

```
*could* be replaced (IF you have the original TA cds) with:
```

int limit = FILE_SIZE_IN_BYTES ;

```
where FILE_SIZE_IN_BYTES is the exact size in bytes of the totala2.hpi file.  This is the only occurance of this function.  Perhaps someone more knowledgeable in c++ could help out on this error.

I had originally thought that this was a freeware game, but it seems you need the original TA cds.  May be worth buying if someone here who owns them can get this working!

---

### Post by 1dude1 on 2008-03-16
hey i tried the 

sudo ln -s /usr/local/lib/allegro /lib/allegro

and i still get the problem allegro is not installed

what else can i do to get this installed

---

### Post by zuzuf on 2008-03-30
Try the last release of TA3D (0.4.2), but it requires a more recent version of Allegro (4.2.2) which is more recent than ubuntu's package (at least for gutsy), so you'll have to install Allegro yourself if you want to build it, but the good news is there are binary packages available for 0.4.2 (built on Kubuntu 7.10, both 32 & 64 bits), so  you should be able to run those binary packages out of the box (it ships required libraries ...)

see [http://ta3d.darkstars.co.uk/linuxdl-en.php](http://ta3d.darkstars.co.uk/linuxdl-en.php)

---

