---
title: "gcc 4.2 installation"
date: 2006-05-30
forum: Desktop Environments
---

### Post by motu on 2006-05-30
hi there 
i'm trying to install the latest version of gcc but i get errors when "making" the program, did anyone installed it successfully?
i get :

```
....
....
gcc -c   -g -DIN_GCC   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition -Wmissing-format-attribute -fno-common -Wno-error  -DHAVE_CONFIG_H -DGENERATOR_FILE -I. -Ibuild -I../.././gcc -I../.././gcc/build -I../.././gcc/../include -I../.././gcc/../libcpp/include  -I../.././gcc/../libdecnumber -I../libdecnumber    -o build/gengtype-lex.o gengtype-lex.c
gcc: gengtype-lex.c : Aucun fichier ou répertoire de ce type
gcc: pas de fichier à l'entrée (no file)
make[3]: *** [build/gengtype-lex.o] Error 1
make[3]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408/host-i686-pc-linux-gnu/gcc »
make[2]: *** [all-stage1-gcc] Error 2
make[2]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408 »
make[1]: *** [stage1-bubble] Error 2
make[1]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408 »
make: *** [all] Error 2

``` 
any idea?

thanks

motu

---

### Post by philippe_carlo on 2006-08-17
Well, it seems like it is trying to build gengtype-lex.o from gengtype-lex.c, but that file is not present. Either this is a bug in the package, or something went wrong wile downloading/unpacking the tarball. 

Is gcc-4.2-20060408/host-i686-pc-linux-gnu/gcc/build/gengtype-lex really there? If not, are there any earlier errors in the compilation process that could prevent this file from being created?

---

### Post by DoktorSeven on 2006-08-17
Possible that it's referring to the fact that the source file needs bison/flex to build (ref [this bug](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=18974)?)

**apt-get install bison flex** and try again?

---

### Post by maubp on 2006-09-03
Looking over at [http://gcc.gnu.org/](http://gcc.gnu.org/) they are still in active development of gcc 4.2, currently at [stage 3](http://gcc.gnu.org/develop.html#stage3) which looks like bug fixing only in preparation for the release of gcc 4.2.0

Based on [previous releases](http://gcc.gnu.org/develop.html#timeline), I would guess the official release is a month away - plus a further delay before its eventually available via and apt-get on ubuntu.

So is the only option (for now) to download a snapshot, and build it myself?

I'm trying this on a 64 machine (see [this thread](http://www.ubuntuforums.org/showthread.php?p=1458037)).

---

### Post by maubp on 2006-09-03
.

---

### Post by ganzhi on 2007-05-11
I googled some prebuild gcc 4.2. But I don't know how to install it. Is it a simple task?
[http://mirror.ne.gov/ubuntu/pool/main/g/gcc-4.2/](http://mirror.ne.gov/ubuntu/pool/main/g/gcc-4.2/)

---

### Post by maubp on 2007-05-11
> **ganzhi said:**
> I googled some prebuild gcc 4.2. But I don't know how to install it. Is it a simple task?
[http://mirror.ne.gov/ubuntu/pool/main/g/gcc-4.2/](http://mirror.ne.gov/ubuntu/pool/main/g/gcc-4.2/)
No idea - but don't do anything rash like reinstalling a more recent libc from source - I had to reinstall that machine!

My plan is to upgrade my ubuntu once the latest version ships with gcc 4.2 (does Feisty Fawn? - I must check)

---

### Post by RedSquirrel on 2007-05-11
> **maubp said:**
> No idea - but don't do anything rash like reinstalling a more recent libc from source - I had to reinstall that machine!

Yeah, it's easier to just install an updated linux distro rather than doing it manually. :)


> **maubp said:**
>  My plan is to upgrade my ubuntu once the latest version ships with gcc 4.2 (does Feisty Fawn? - I must check)

feisty has 4.1.2

Just out of curiosity, why do you guys want something newer than that?

---

### Post by maubp on 2007-05-13
> **RedSquirrel said:**
> feisty has 4.1.2
Grr :(
> **RedSquirrel said:**
> Just out of curiosity, why do you guys want something newer than that?
I want GOMP, included in gcc 4.2, because OpenMP looks like a nice way to do parallel programming on multicore machines.
[http://gcc.gnu.org/gcc-4.2/changes.html](http://gcc.gnu.org/gcc-4.2/changes.html)

---

### Post by ganzhi on 2007-05-15
Yes, openmp is the killer feature of gcc 4.2. I felt envy cause Fedora 6 user can enjoy it.

---

### Post by maubp on 2007-05-15
I knew RedHat had back ported the OpenMP support to gcc 4.1, but as far as I know none of the other distributions have done this.

On the bright side, the next Ubuntu release, Gutsy Gibbon, will have gcc 4.2 (but that's about six months off).

P.S. You can get the Intel compiler free (as in beer, not as in freedom) for personal use. There are threads on her somewhere about that.

---

### Post by tkjacobsen on 2007-05-17
There is a build form May 16th in the gusty repos.. Maybe I will upgrade early again, bacause I'm having a parallel computing course from September 1st.

---

### Post by ganzhi on 2007-05-21
Hi, tkjacobsen

Can you share your experience when you've done it?

---

### Post by godvirus on 2007-05-21
Yes, I would like to install g++-4.2 also. Can someone please make packages available for feisty kubuntu?

Thank you!

---

### Post by AzraelUK on 2007-05-30
I need GCC 4.2.0 because of this:
```
peter@N00B-PC:~$ cd darwinia-demo2/
peter@N00B-PC:~/darwinia-demo2$ ./darwinia 
.
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
peter@N00B-PC:~/darwinia-demo2$ 
```

I have no idea how this happened. I wish I'd never upgraded to feisty :/

---

### Post by gizmoarena on 2007-06-25
the problem is not with your fiesty. I guess you have tried to install gcc 4.2 with some error or something.

---

### Post by glangollor on 2007-07-11
> **motu said:**
> hi there 
i'm trying to install the latest version of gcc but i get errors when "making" the program, did anyone installed it successfully?
i get :

```
....
....
gcc -c   -g -DIN_GCC   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition -Wmissing-format-attribute -fno-common -Wno-error  -DHAVE_CONFIG_H -DGENERATOR_FILE -I. -Ibuild -I../.././gcc -I../.././gcc/build -I../.././gcc/../include -I../.././gcc/../libcpp/include  -I../.././gcc/../libdecnumber -I../libdecnumber    -o build/gengtype-lex.o gengtype-lex.c
gcc: gengtype-lex.c : Aucun fichier ou répertoire de ce type
gcc: pas de fichier à l'entrée (no file)
make[3]: *** [build/gengtype-lex.o] Error 1
make[3]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408/host-i686-pc-linux-gnu/gcc »
make[2]: *** [all-stage1-gcc] Error 2
make[2]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408 »
make[1]: *** [stage1-bubble] Error 2
make[1]: leaving directory « /home/motu/Desktop/gcc/gcc-4.2-20060408 »
make: *** [all] Error 2

``` 
any idea?

thanks

motu

Yes... 
I had the same error and googling for it I found your thread. 
Since knowing somebody else hab the problem I got motivated to read [http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html)
again. And after some reading I added 
--enable-generated-files-in-srcdir 
to my config options.
My next error was overcome with --disable-multilib ....
An now it is compiling since quite a while....
Perhaps thats why  I wrote such a long reply.... not even knowing my compilation will be successful:-)
:)
You'll here of me when its done!

---

### Post by glangollor on 2007-07-11
well it works now.... I did:
```
    ../configure   --prefix=/usr/local/gcc-4.2-20070627    --enable-threads=posix --with-system-zlib --enable-__cxa_atexit  --disable-checking --disable-nls    --enable-bootstrap  --with-gcc --with-gnu-as --with-gnu-ld --enable-generated-files-in-srcdir --disable-multilib 
```
I already did some openmp stuff with it.....

---

