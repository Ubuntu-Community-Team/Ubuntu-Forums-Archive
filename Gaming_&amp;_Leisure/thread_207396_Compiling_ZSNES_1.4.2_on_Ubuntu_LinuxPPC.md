---
title: "Compiling ZSNES 1.4.2 on Ubuntu Linux/PPC"
date: 2006-07-01
forum: Gaming &amp; Leisure
---

### Post by RavenOfOdin on 2006-07-01
Has anyone else had as many problems as I have trying to compile this?
I downloaded their source file and all I see in there besides aclocal and autoconf is a line which says:

```

sh ./autogen.sh && gmake && gmake install

```

then:

```

./configure $*

```

Since there is no "gmake" -- at least not that I know of -- I had to change that to "make". . .then the --target option for configure doesn't work and it keeps coming back as "compiling for 386."

After downloading the most recent version of g++, sans dummy package, I symlinked g++-4.0.3 to g++ in my /usr/bin folder.  Then the conf script picked up g++ and everything went well until the "jma" files and the lump compilation into one executable.  The error warning I got was:

```

/usr/bin/ld: chips/sfxproc.o: Relocations in generic ELF (EM: 3)
chips/sfxproc.o: could not read symbols: File in wrong format.
collect2: ld returned 1 exit status

```

and make bailed.

I have OpenGL support enabled and am using --target directives (set to powerpc-linux) as well as the CXXFLAGS directive -mcpu=powerpc.  It still doesn't work and still compiles for 386.

NASM is installed, as are libSDL and its dev libraries. 

Can anyone help me to compile this correctly so I can start playing SNES games?

(PS: Instead of "/share/aclocal", the entry for aclocal is already set to /usr/share/aclocal for a standard Ubuntu install.)

---

### Post by FallenWizard on 2006-07-02
hm.. There is a zsnes package already in multiverse, but ok :)

First, put this in the console:

```
sudo apt-get install libsdl1.2-dev libpng12-dev nasm zlib1g-dev
```

Then just compile the emulator with:

./configure
make
sudo make install

and it should work



EDIT: Oh, I didn't saw that you are using PowerPC, I don't know how it works, can you try it?
EDIT2: I am blind, @Mods, delete this post please :-?

---

### Post by RavenOfOdin on 2006-07-02
Forget it, I went ahead and installed snes9x-x and snes9express off archive.ubuntu.com.  It works.

---

### Post by Gnobody on 2006-07-02
AFAIK ZSNES is written in x86 assembly language so it may be impossible.

---

### Post by jim1337 on 2006-07-04
i was able to get it to work

Use the following commands

sudo apt-get install libsdl1.2-dev libpng12-dev nasm zlib1g-dev
./configure 
make

i did that and i was able to do it

---

### Post by alex_0077 on 2007-03-07
:popcorn: 

EDIT: whoa, I hadnt noticed this thread was old.

Using the synaptec package manager, I installed the following to get ZNES to work on Xubuntu (aka Ubuntu w/ XFCE)

NOTE: I don't know if all are necessary, I just added whatever (i thought) the compiler was looking for when it crashed.


Just add whatever the "znes_1_51/docs/install.txt" file asks you for your computer, and then check to make sure the following are installed in the Synaptec package manager before using their "znes_1_51/src/autogen.sh" file.

autoconf
automake1.9
autotools-dev
dosemu             (not sure if I needed this one)
g++
g++-3.3
g++-4.1
gcc-3.3
gcc-3.3-base
gcc-3.4-base
gcc-4.1
gcc-4.1-base
libgcc1
libpng12-0
libpng12-dev
libsdl1.2debian
libsdl1.2debian-all
libsdl1.2-dev
libsdl-gfx1.2-4
libsdl-gfx1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev
libsdl-net1.2
libsdl-net1.2-dev
libsdl-ttf2.0-0
libsdl-ttf2.0-dev
make
p7zip (to be able to extract roms compressed with 7zip)

Once you finish making sure the above packages are installed, run their autogen.sh file, and run the "make" command.

YOU SHOULD NOW HAVE AN EXECUTABLE, IT WILL BE "znes_1_51/src/znes"

Let me know if I missed something.

---

### Post by pagefault on 2007-06-21
It is impossible to run ZSNES on a PPC. It is an x86 program.

---

### Post by Aglari on 2008-02-26
I followed the instructions in the second post, but got an error when i tried 'make':

```
alex@snowfield:~/Downloads/zsnes_1_42/src$ make
nasm  -w-orphan-labels -D__LINUX__ -f elf -DELF -D__OPENGL__ -O1 -o chips/sfxproc.o chips/sfxproc.asm
nasm: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.7' not found (required by nasm)
make: *** [chips/sfxproc.o] Error 1

```

I'm pretty new at this, so i have no idea where to go from here. Any help would be great.

Also, i know v1.51 is in synaptic, but i want v1.42 for netplay

---

### Post by Aglari on 2008-02-27
ah, nevermind, i got it off of archive.ubuntu.com

---

### Post by kortez on 2008-07-16
Hi, I have the zsnes deb files and everything for version 1.42, and i want to install it but it will not install unless i uninstall 1.51. I don't have a problem with this except I do not want to lose my saved states for super mario rpg. Is there a way to remove 1.51 without removing the save files? And if so, how do I, use those save files with 1.42.
Thankyou.

---

### Post by acoustibop on 2008-07-16
Your save states should be saved in ~/.zsnes, I think, kortez, unless you've set ZSNES to save them in a different location (as I do).  See what you have set in Config -> Paths.  Either way, uninstalling ZSNES should not remove them, although if you want to be sure, back them up.

Your new installation should find them again if they're in the default location; if not, you'll have to point ZSNES at them again.  I'm not sure about save states, but regular saves should work fine between versions.

---

