---
title: "HELP!!! i need to compile and run Quake 2 from source code"
date: 2010-12-30
forum: Gaming &amp; Leisure
---

### Post by auroraa9420 on 2010-12-30
yes i cant compile and run quake 2

here is my command line

auroraa9420@Auroraa9420:~/quake2-3.21/linux$ sudo make
mkdir: cannot create directory `debugi386-glibc': File exists
mkdir: cannot create directory `debugi386-glibc/client': File exists
mkdir: cannot create directory `debugi386-glibc/ded': File exists
mkdir: cannot create directory `debugi386-glibc/ref_soft': File exists
mkdir: cannot create directory `debugi386-glibc/ref_gl': File exists
mkdir: cannot create directory `debugi386-glibc/game': File exists
mkdir: cannot create directory `debugi386-glibc/ctf': File exists
make: [build_debug] Error 1 (ignored)
make targets BUILDDIR=debugi386-glibc CFLAGS="-Dstricmp=strcasecmp -g"
make[1]: Entering directory `/home/auroraa9420/quake2-3.21/linux'
gcc -Dstricmp=strcasecmp -g -o debugi386-glibc/client/sys_linux.o -c ../linux/sys_linux.c
../linux/sys_linux.c: In function ‘Sys_GetGameAPI’:
../linux/sys_linux.c:227: error: #error Unknown arch
../linux/sys_linux.c:238: error: ‘gamename’ undeclared (first use in this function)
../linux/sys_linux.c:238: error: (Each undeclared identifier is reported only once
../linux/sys_linux.c:238: error: for each function it appears in.)
make[1]: *** [debugi386-glibc/client/sys_linux.o] Error 1
make[1]: Leaving directory `/home/auroraa9420/quake2-3.21/linux'
make: *** [build_debug] Error 2


!!!WHAT SHOULD I DO!!!

---

### Post by gordintoronto on 2010-12-30
"!!!WHAT SHOULD I DO!!!"

Run Quake Live!

---

### Post by rajeev1204 on 2010-12-30
> **auroraa9420 said:**
> yes i cant compile and run quake 2

here is my command line

auroraa9420@Auroraa9420:~/quake2-3.21/linux$ sudo make
mkdir: cannot create directory `debugi386-glibc': File exists
mkdir: cannot create directory `debugi386-glibc/client': File exists
mkdir: cannot create directory `debugi386-glibc/ded': File exists
mkdir: cannot create directory `debugi386-glibc/ref_soft': File exists
mkdir: cannot create directory `debugi386-glibc/ref_gl': File exists
mkdir: cannot create directory `debugi386-glibc/game': File exists
mkdir: cannot create directory `debugi386-glibc/ctf': File exists
make: [build_debug] Error 1 (ignored)
make targets BUILDDIR=debugi386-glibc CFLAGS="-Dstricmp=strcasecmp -g"
make[1]: Entering directory `/home/auroraa9420/quake2-3.21/linux'
gcc -Dstricmp=strcasecmp -g -o debugi386-glibc/client/sys_linux.o -c ../linux/sys_linux.c
../linux/sys_linux.c: In function ‘Sys_GetGameAPI’:
../linux/sys_linux.c:227: error: #error Unknown arch
../linux/sys_linux.c:238: error: ‘gamename’ undeclared (first use in this function)
../linux/sys_linux.c:238: error: (Each undeclared identifier is reported only once
../linux/sys_linux.c:238: error: for each function it appears in.)
make[1]: *** [debugi386-glibc/client/sys_linux.o] Error 1
make[1]: Leaving directory `/home/auroraa9420/quake2-3.21/linux'
make: *** [build_debug] Error 2


!!!WHAT SHOULD I DO!!!


I assume you have installed the package build-essential.Are you compiling on 64 bit?

---

### Post by rajeev1204 on 2010-12-30
> **gordintoronto said:**
> "!!!WHAT SHOULD I DO!!!"

Run Quake Live!

What has this got to do with the OP's question ?

---

### Post by auroraa9420 on 2010-12-31
> **rajeev1204 said:**
> I assume you have installed the package build-essential.Are you compiling on 64 bit?

yes im runing it on 64 bit

---

### Post by DoktorSeven on 2010-12-31
Where did you get the source?  Possible that the original id supplied source will not compile on 64bit.

Try the one from Icculus [http://icculus.org/quake2/](http://icculus.org/quake2/) or another source update.

---

### Post by auroraa9420 on 2011-01-01
> **DoktorSeven said:**
> Where did you get the source?  Possible that the original id supplied source will not compile on 64bit.

Try the one from Icculus [http://icculus.org/quake2/](http://icculus.org/quake2/) or another source update.

thank you!!!

i get a lot more input buy downloading your version but i get a new error

make[1]: *** [releasex86_64/client/cd_sdl.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: Leaving directory `/home/auroraa9420/src'
make: *** [build_release] Error 2

---

### Post by auroraa9420 on 2011-01-01
TYPO

i whanted to say output

---

### Post by Rustybolts on 2011-01-01
Why don't you just run it with Yamagi?
[http://www.yamagi.org/quake2/](http://www.yamagi.org/quake2/)

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> Why don't you just run it with Yamagi?
[http://www.yamagi.org/quake2/](http://www.yamagi.org/quake2/)

1.i whant to make a engine mod, that way i will get more experience

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> Why don't you just run it with Yamagi?
[http://www.yamagi.org/quake2/](http://www.yamagi.org/quake2/)

that code that you gave me is great please tell me how to install the pak0 :D

---

### Post by auroraa9420 on 2011-01-01
bump

---

### Post by auroraa9420 on 2011-01-01
> **auroraa9420 said:**
> bump

i have installed it and all i get is a black screen and nothing more, i was trying with different renders and still nothing

---

### Post by Rustybolts on 2011-01-01
> **auroraa9420 said:**
> that code that you gave me is great please tell me how to install the pak0 :D
[http://www.yamagi.org/quake2/debian.html]("http://www.yamagi.org/quake2/README")

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> [http://www.yamagi.org/quake2/README](http://www.yamagi.org/quake2/README)

still i have the same problem as before

---

### Post by Rustybolts on 2011-01-01
I have changed the link its [http://www.yamagi.org/quake2/debian.htm]("http://www.yamagi.org/quake2/debian.html")l

Quoted from link above (the links inside this quote are clickable)
> **Downloads**

                          The most recent versions of the binary packages are linked. 
            If you want an older version or the packages sources (to build your own packages              for another architecture or whatever) look              [**here**]("http://deponie.yamagi.org/quake2/debs/"). 
            
            **Newest stable version:**
            **yamagi-quake2:**                  [i386]("http://deponie.yamagi.org/quake2/debs/i386/yamagi-quake2_2.11-1_i386.deb")                  [amd64]("http://deponie.yamagi.org/quake2/debs/amd64/yamagi-quake2_2.11-1_amd64.deb")                 
            **quake2-data (still old version):**                  [all architectures]("http://deponie.yamagi.org/quake2/debs/all/quake2-data_16_all.deb") 
            **yamagi-quake2-addons:**                  [i386]("http://deponie.yamagi.org/quake2/debs/i386/yamagi-quake2-addons_1.1_i386.deb")                  [amd64]("http://deponie.yamagi.org/quake2/debs/amd64/yamagi-quake2-addons_1.1_amd64.deb")                  

                         For your convenience I created tarballs containing the latest             version of all three packages for amd64 und i386.
            Newest stable version:
            [All-in-One package for i386]("http://deponie.yamagi.org/quake2/debs/yamagiq2-allinone-i386.tar.gz") 
            [All-in-One package for amd64]("http://deponie.yamagi.org/quake2/debs/yamagiq2-allinone-amd64.tar.gz") 
            
                          **Installation**

                          After you have downloaded the packages you want to install, you may install them via
            **$ dpkg -i /your/path/to/packages/PACKAGE.deb**
            where PACKAGE.deb should be replaced by the package you want to              install, for example "yamagi-quake2_1.05-1_i386.deb".
            You need root privileges to do this, so become root or place "sudo"             in front of the command.
            
            The executables and game libs will be installed to /usr/lib/games/yamagi-quake2/.
            The game data (levels, videos, ...) are expected to be located in /usr/share/games/quake2/             
            
            For further information (on how to install the game data etc) see              /usr/share/doc/yamagi-quake2/README.Debian and              /usr/share/doc/yamagi-quake2-addons/README.Debian             **after** installing the package(s).

If you have full version you can place them at /home/[COLOR=Red]YOUR_USERNAME_HERE[/COLOR]/.quake2

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> I have changed the link its [http://www.yamagi.org/quake2/debian.htm]("http://www.yamagi.org/quake2/debian.html")l

Quoted from link above (the links inside this quote are clickable)


If you have full version you can place them at /home/[COLOR=Red]YOUR_USERNAME_HERE[/COLOR]/.quake2

weard, nether of the packs work

do you have team viewer or msn to help me

---

### Post by Rustybolts on 2011-01-01
are you running 32 or 64 bit ubuntu?

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> are you running 32 or 64 bit ubuntu?

64 bit

---

### Post by Rustybolts on 2011-01-01
[COLOR=Blue]click this[/COLOR] [http://deponie.yamagi.org/quake2/debs/amd64/yamagi- quake2_2.11-1_amd64.deb]("http://deponie.yamagi.org/quake2/debs/amd64/yamagi-quake2_2.11-1_amd64.deb") [COLOR=Blue]and select install with ubuntu software centre[/COLOR]
[COLOR=Blue]Then this[/COLOR]
[http://deponie.yamagi.org/quake2/debs/all/quake2-data_16_all.deb](http://deponie.yamagi.org/quake2/debs/all/quake2-data_16_all.deb) [COLOR=Blue]do the same[/COLOR]

---

### Post by auroraa9420 on 2011-01-01
> **Rustybolts said:**
> [COLOR=Blue]click this[/COLOR] [http://deponie.yamagi.org/quake2/debs/amd64/yamagi- quake2_2.11-1_amd64.deb]("http://deponie.yamagi.org/quake2/debs/amd64/yamagi-quake2_2.11-1_amd64.deb") [COLOR=Blue]and select install with ubuntu software centre[/COLOR]
[COLOR=Blue]Then this[/COLOR]
[http://deponie.yamagi.org/quake2/debs/all/quake2-data_16_all.deb](http://deponie.yamagi.org/quake2/debs/all/quake2-data_16_all.deb) [COLOR=Blue]do the same[/COLOR]

thank you!!!

the problem wasnt in the source code, it was the pak0 that i had...it was corupt :D

---

### Post by Rustybolts on 2011-01-02
Your welcome!

---

### Post by gpwil1 on 2011-03-02
Hi All,

Most mods were never ported to linux and are unplayable with the native linux client, since they use the game.so and not the game86.dll. 

If you are like me and you desperately want to play native q2 but still want to play some of those mods, a really nasty - but working way is to do the following:

copy the pak files into a folder and install the yamagi and 
q2-3.20-x86-full.exe patch for quake2 (this contains all the required dll's and exe's). install the mods as per usual to the /usr/share/games/quake/blah directory.

run the quake2.exe with wine as a dedicated server with +set game blah

then use the native linux client to connect to the game.

Ugly, but it works.

g


edit - also it probably wont like connecting to "localhost" if you are not connected to a network, simply use 127.0.0.1

---

