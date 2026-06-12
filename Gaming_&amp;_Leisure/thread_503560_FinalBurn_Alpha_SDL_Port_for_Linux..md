---
title: "FinalBurn Alpha SDL Port for Linux."
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by KingHanco on 2007-07-18
Ok I need help on making FBA SDL for Ubuntu.

```
KEV wrote:needs (at least) SDL, gcc, g++, perl, nasm, zlib, libpng and a unix like enviroment, I guess.
```

Here is his source. [http://www.kja.pwp.blueyonder.co.uk/fbasdl.zip](http://www.kja.pwp.blueyonder.co.uk/fbasdl.zip)

Also please read 1 page through 10 page. [http://www.ojko.com/phpbb/viewtopic.php?f=3&t=2067&st=0&sk=t&sd=a](http://www.ojko.com/phpbb/viewtopic.php?f=3&t=2067&st=0&sk=t&sd=a)

Let me know if you get it to make and work. Be sure to help me out. Thanks.

I will post this link at that forum to point KEV here.

---

### Post by KingHanco on 2007-07-18
How to setup a build environment?

---

### Post by DoktorSeven on 2007-07-18
**sudo apt-get install build-essential**

---

### Post by KingHanco on 2007-07-18
Ok now how I run make on makefile.sdl? "/home/mitchell/fbasdl"

---

### Post by KingHanco on 2007-07-26
Ok I can run make now. But I'm missing some SDL files.

```
mitchell@pc-desktop:~$ cd /home/mitchell/fbasdl
mitchell@pc-desktop:~/fbasdl$ make -f makefile.sdl
Making debug build...

Generating depend file for src/burner/sdl/main.cpp...
/bin/sh: sdl-config: not found
In file included from src/burner/burner.h:31,
                 from src/burner/sdl/main.cpp:13:
src/burner/sdl/burner_sdl.h:1:17: error: SDL.h: No such file or directory
make: *** [main.d] Error 1
```

What do I need to download to get those missing files?

---

### Post by DoktorSeven on 2007-07-26
sudo apt-get install libsdl1.2-dev

Any time you see a build ask for files from a certain thing like "SDL.h", search for the main part (without the .h, in this case SDL) and add "dev" in apt-cache search:

**apt-cache search sdl dev**

Install the most likely candidate; it should have **-dev** at the end of the package name.

---

### Post by KingHanco on 2007-07-26
Ok this is hard part.

```
Generating src/generated/ctv.h...
/bin/sh: cannot create src/generated/ctv.h: Permission denied
make: *** [src/generated/ctv.h] Error 2
```

So far I download.

```
sudo apt-get install build-essential
sudo apt-get install libsdl1.2-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libglpng-dev
```

---

### Post by DoktorSeven on 2007-07-26
Probably don't have correct permissions, happens sometimes when I extract a source package from zip:

**chmod -R 777 *** from where the source is extracted.   777 might be a little overkill, but it'll ensure you (and the build process) can write to everything. :)

---

### Post by KingHanco on 2007-07-26
Done now.

It made fbasdld.

Run these bellow into "Terminal".

```
sudo apt-get install build-essential
sudo apt-get install libsdl1.2-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libglpng-dev
sudo apt-get install nasm
cd /home/<Your Name>/fbasdl
chmod -R 777 /home/<Your Name>/fbasdl
make -f makefile.sdl
```

Never mind. KEV told me to run like this. "Run ./fbasdl punisher or whatever."

---

### Post by NigiAtP on 2009-08-27
Did everything as described above and ended up with:
```
>make -f makefile.sdl
Making debug build...

Assembling src/burn/burn_sound_a.asm...
src/burn/burn_sound_a.asm:464: error: mismatch in operand sizes
src/burn/burn_sound_a.asm:526: error: mismatch in operand sizes
src/burn/burn_sound_a.asm:599: error: mismatch in operand sizes
make: *** [burn_sound_a.o] Error 1
```
Any suggestions?

---

