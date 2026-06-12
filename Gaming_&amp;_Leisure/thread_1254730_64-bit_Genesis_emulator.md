---
title: "64-bit Genesis emulator"
date: 2009-08-31
forum: Gaming &amp; Leisure
---

### Post by gamelord12 on 2009-08-31
I have 64-bit Ubuntu, but I can't find a Genesis emulator that will work with it.  I compile some by source, but during the compile, most specifically mention that they don't support 64-bit architectures.  The only ones that actually run are Regen and Dgen, but Regen locks up when I try to load a ROM and Dgen seg faults when I try to run it.  Are there no 64-bit compatible Genesis emulators for Linux?

---

### Post by BoyOfDestiny on 2009-08-31
MESS emulates about 340 different systems, not all of them perfectly mind you.
[MESS]("http://mess.redump.net/")

Linux/Unix port:
[SDLMESS]("http://rbelmont.mameworld.info/?page_id=163") 

The Genesis support is good IMHO.

Anyway, it needs to be compiled, and should work fine on multiple architectures.

---

### Post by gamelord12 on 2009-08-31
According to the wikipedia page for MESS, I need to download the ROM chip data for any system I want to emulate.  Where would I even begin to find that?  Will it emulate Genesis just fine without additional files?

---

### Post by BoyOfDestiny on 2009-08-31
Well, to answer your first question, you'd need a search engine as it's beyond the scope of this forum. ;) 

To answer your second question, MESS can run the genesis without that file.

Once you have everything compiled

```
./mess genesis -cartridge yourfile.gen
```

Replace yourfile.gen with whatever the name of the game file is...

---

### Post by wingnux on 2009-09-01
Have you tried Gens/GS? It's the best genesis emulator around.

---

### Post by disturbedite on 2009-09-01
> **wingnux said:**
> Have you tried Gens/GS? It's the best genesis emulator around.

you missed the point: it is only 32bit.

---

### Post by wingnux on 2009-09-01
IIRC it runs just fine on 64bit, you may just need to get some additional libs but that's what "getlibs" is for ;)

---

### Post by CharmyBee on 2009-09-01
That didn't work for me. The best I can do is just wine the windows Gens/GS. :(

Also, MESS is not a viable substitute.

---

### Post by hikaricore on 2009-09-01
32 bit Gens runs fine on a 64 bit system with 32bit libs.
Perhaps you're not doing it right.

I do agree tho MESS is not a reasonable solution, major case of the name fitting perfect.

---

### Post by gamelord12 on 2009-09-01
When compiling sdlmess, I get a whole mess of errors, probably because it's looking for a package gtk+-2.0

---

### Post by gamelord12 on 2009-09-01
Btw, when I try to run ./configure for Gens/GS, it doesn't tell me what 64-bit libs it doesn't work with.  It just says 64-bit isn't supported.

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for library containing strerror... none required
checking for ANSI C header files... (cached) yes
configure: error: 64-bit is currently not supported.
```

---

### Post by wingnux on 2009-09-01
Install it from the deb package with the "--force-architecture" option and then install the necessary 32-bit libs using getlibs.

---

### Post by BigSilly on 2009-09-02
I made a 64 bit package using a 32 bit conversion script I found on the World of Goo forums. I think I've posted it up before, but I don't mind attaching it here again. Hope it works for you. It's fine on mine!

---

### Post by sherl0k on 2009-09-02
Oh awesome, thanks! I agree MESS is not a decent solution. I appreciate all the work they do with that but it's a real pain getting games to work, and it's lacking some good features most other emulators have.

---

### Post by gamelord12 on 2009-09-02
Let's say I wanted to do this in the future; how do I use getlibs?  How do I know which libraries it needs 32-bit versions of?

---

### Post by wingnux on 2009-09-02
Download/install getlibs: [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

Run the program from the terminal and it'll complain about a missing library, copy it's name and then run "getlibs -32 (or 64, depends on the lib architecture) libfile". I had to run "getlibs -32 libgtk-1.2.so.0" in order to get ePSXe to run on Jaunty 32bits.

---

### Post by farrell2k on 2009-09-02
I would not use anything but XE.  It emulates everything perfectly.  I have not found a game or sega cd that would not work on it.

xe-emulator.com

---

### Post by hikaricore on 2009-09-02
> **farrell2k said:**
> I would not use anything but XE.  It emulates everything perfectly.  I have not found a game or sega cd that would not work on it.

xe-emulator.com

Never even heard of it.
I assume since it supports so many systems it's like mednafen and uses other emulator source as its base?

---

### Post by Grishka on 2009-09-03
> **hikaricore said:**
> Never even heard of it.
I assume since it supports so many systems it's like mednafen and uses other emulator source as its base?

no.

---

### Post by hikaricore on 2009-09-03
> **Grishka said:**
> no.

Thanks for the detailed reply.. :p

---

### Post by Grishka on 2009-09-03
> **hikaricore said:**
> Thanks for the detailed reply.. :p

you are most welcome. :p details [here](http://xe-emulator.com/index.php?m=about).

---

