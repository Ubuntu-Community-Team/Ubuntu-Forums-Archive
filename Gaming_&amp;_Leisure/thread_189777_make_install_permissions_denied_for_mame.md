---
title: "make install permissions denied for mame"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by T313C0mun1s7 on 2006-06-05
I am installing mame from source (downloaded as of yesterday) and the make portion went ok, but not make install. I am not extreamly familiar with installing from source, but I have done it a couple of times under slackware.

If I can remember correctly it goes like this:[LIST]
[*]become root
[*]./configure
[*]make
[*]make install[/LIST]there is no configure file so I made the modifications to the Makefile manually, the make seemed to go ok. I got warnings but did not see any errors. Then when I tried make install I get this:
```
Installing binaries under /usr/local/bin...
/usr/local/install -d -o root -g bin -m  755 /usr/local/bin
make: execvp: /usr/local/install: Permission denied
make: [doinstall] Error 127 (ignored)
/usr/local/install -c -o root -g bin -m  555 xmame.x11 /usr/local/bin
make: execvp: /usr/local/install: Permission denied
make: *** [doinstall] Error 127

``` 
The permissions on the /usr/local/install directory are 777, and as I said I am root (via the "Root Terminal" icon in the Applications menu under System Tools. Any assistance is appreciated. Thank you

---

### Post by T313C0mun1s7 on 2006-06-06
So am I in the wrong forum for this? MAME is a game hardware emulator, so I thought this would be the place. Could someone at least suggest which forum I might try to have a better change at a reply?

---

### Post by seth0x2b on 2006-06-06
How exactly are you becoming root?!
This would be a correct compile sequence:
```

extract source archive.
goto to the extracted archive's folder

./configure
make
**sudo **make install

``` 

Cheers

---

### Post by T313C0mun1s7 on 2006-06-06
I am in a terminal windows as root.

[quote=T313C0mun1s7]. . . and as I said I am root (via the "Root Terminal" icon in the Applications menu under System Tools.[/quote] 
So then I got there via **[FONT=System]Applications --> System Tools --> Root Terminal[/FONT]**

I have a # at the end of the prompt and a prompt of:
```
root@powerhouse:/usr/src/xmame-0.106#
```

---

### Post by seth0x2b on 2006-06-06
Sorry...I skipped the end of your initial post. But still, you could try with [B]sudo.
[/B]Other than that, I have no ideea ](*,)

Cheers and good luck

---

### Post by engla on 2006-06-06
Packages without a configure file can be complicated..

it looks like it expects to find the 'install' program at /usr/local/install, while it is really at /usr/bin/install. This probably means that you have to tweak the Makefile further, either finding that explicit path, or making sure that prefix is /usr, exec_prefix is /usr/bin etc etc.. the only way to know what exactly to do is to read the Makefile.

---

### Post by T313C0mun1s7 on 2006-06-07
Ah Ha, thank you engia for such a great reply. I thought it was looking for a location to install to, and after a precursory glance in the /usr/bin directory and not finding an install directory I created a directory under /usr/local called install, and changed the makefile.

So in all it seems it is MY FAULT. There of course is an executable in the /usr/bin directory named install. I will fix the Makefile and report back.

---

### Post by T313C0mun1s7 on 2006-06-07
The make install finished ok, but I am not sure I did it correctly.

My processor is an AMD Athlon64 X2, but I am running and wanting to compile for 32 bit. So I may have my processor incorrect in the Makefile. I am not sure what to select to build 32 bit but still get all the features and optimizations I can out of the build. I am also getting other errors, but I think that they may be related to the fact that I have not yet copied any roms into the location it will be looking for them.

> **output of make install and running the executable]root@powerhouse:/usr/src/xmame-0.106# make install
Installing binaries under /usr/local/bin...
/usr/bin/install -d -o root -g bin -m  755 /usr/local/bin
/usr/bin/install -c -o root -g bin -m  555 xmame.x11 /usr/local/bin
/usr/bin/install -c -o root -g bin -m  555 romcmp chdman xml2info jedutil /usr/local/bin
Installing manual pages under /usr/local/man/man6 ...
/usr/bin/install -d -o root -g bin -m  755 /usr/local/man/man6
/usr/bin/install -c -o root -g bin -m  444 src/unix/doc/xmame.6 /usr/local/man/man6/xmame.6
*** xmame for linux-amd64 installation completed***
root@powerhouse:/usr/src/xmame-0.106# xmame.x11
info: trying to parse: /usr/local/share/xmame/xmamerc
info: trying to parse: /root/.xmame/xmamerc
info: trying to parse: /usr/local/share/xmame/xmame-x11rc
info: trying to parse: /root/.xmame/xmame-x11rc
info: trying to parse: /usr/local/share/xmame/rc/robbyrc
info: trying to parse: /root/.xmame/rc/robbyrc
loading rom 0: rotox1.bin
loading rom 1: rotox2.bin
loading rom 2: rotox3.bin
loading rom 3: rotox4.bin
loading rom 4: rotox5.bin
loading rom 5: rotox6.bin
loading rom 6: rotox7.bin
loading rom 7: rotox8.bin
loading rom 8: rotox9.bin
loading rom 9: rotox10.bin
done
rotox1.bin   NOT FOUND
rotox2.bin   NOT FOUND
rotox3.bin   NOT FOUND
rotox4.bin   NOT FOUND
rotox5.bin   NOT FOUND
rotox6.bin   NOT FOUND
rotox7.bin   NOT FOUND
rotox8.bin   NOT FOUND
rotox9.bin   NOT FOUND
rotox10.bin  NOT FOUND
ERROR: required files are missing, the game cannot be run.
[/quote] 

Below is my Makefile (I cut out the header comments because this post was to long):
```

###########################################################################
# Xmame or xmess or...?
###########################################################################

# Uncomment one of these.
TARGET = mame
# TARGET = mess
# TARGET = mage
# TARGET = mmsnd
# example for a tiny compile
# TARGET = tiny


###########################################################################
# Special features
###########################################################################

# Enable experimental network support.  See 
# src/unix/doc/multiplayer-readme.txt for more information.  (CURRENTLY 
# BROKEN)
# XMAME_NET = 1

# Uncomment to use DRC MIPS3 engine (faster emulation, but only works on x86-
# compatible CPUs).
X86_MIPS3_DRC = 1

# Uncomment to use DRC PowerPC engine (faster emulation, but only works on x86-
# compatible CPUs).
X86_PPC_DRC = 1

# Uncomment to use DRC Voodoo rasterizers (faster emulation, but only works on 
# x86-compatible CPUs).
X86_VOODOO_DRC = 1

# Uncomment to disable effects.  This can considerably speed up compilation of 
# the blit files.
# DISABLE_EFFECTS = 1

# Uncomment the line below to enable the MMX assembly-language optimized
# routines for the "light scanlines" and "6-tap filter" effects. This
# requires an IA-32 processor with MMX capability and the NASM assembler.
#
# On Linux-i386 you can enable this without causing problems on non
# MMX capable processors: the Linux code will autodetect if an MMX
# capable processor is present and use the right code.
EFFECT_MMX_ASM = 1


###########################################################################
# Development environment options 
###########################################################################

# GNU make is MANDATORY!!!


###########################################################################
# Choose your compiler.
###########################################################################

# Support for the Intel C++ Compiler is new and experimental.  Be sure
# to check the CFLAGS, RANLIB, IL, LD, and MY_CPU sections in this 
# makefile.  If you've set up a nice environment or alias or wrapper
# script, then you can use `icc'.
#
# Use of `c89' is recommend for Ultrix as it generates faster code, which
# means fewer frames to be skipped and better graphics, but `gcc' works 
# just as well.  However, stay away from the `cc' Ultrix compiler if 
# possible.

CC    = @gcc
# CC    = @cc
# CC    = @icc
# CC    = @c89

# Uncomment for Sun Forte 7 and above C/C++ compiler, see below for
# additional optimizations.
# CC = @sun-forte

# Compiler for host compilations in cross-compiling environments (used 
# in src/unix/unix.mak for m68k).
HOST_CC = $(CC)
# HOST_CC = @gcc


###########################################################################
# Reset CFLAGS
###########################################################################

# If you want to use whatever CFLAGS are currently set in your 
# environment, then comment this out.
CFLAGS =


###########################################################################
# Choose from some preset CFLAGS.  Or, if you want to tweak some more, skip
# this section.
###########################################################################

# GCC on x86
CFLAGS = -O2

# GCC on x86 with some optimizations
# CFLAGS = -O2 -mtune=i686 -fomit-frame-pointer -fstrength-reduce -ffast-math

# GCC on Linux/PowerPC
# CFLAGS = -O2 -funroll-loops -fstrength-reduce -fomit-frame-pointer \
#     -ffast-math -fsigned-char -mlongcall

# GCC on OpenStep/Intel
# CFLAGS = -O2 -finline-functions -ffast-math -fstrength-reduce \
#     -traditional-cpp

# GCC on OpenStep/PPC or Mac OS X.
# CFLAGS = -O2 -funroll-loops -fstrength-reduce -fomit-frame-pointer \
#   -ffast-math -fsigned-char

# IRIX MIPSpro R5+K without IPA
# CFLAGS = -n32 -mips4 -O3 -OPT:Olimit=0

# IRIX MIPSpro with really serious optimization for R10K O2
# CFLAGS = -fullwarn -n32 -mips4 -Ofast=ip32_10k -TARG:platform=ip32_10k \
#   -OPT:Olimit=0 -IPA

# IRIX with more general optimization for R5+K MIPS machines
# CFLAGS = -fullwarn -n32 -mips4 -Ofast -OPT:Olimit=0 -IPA

# IRIX with R4K MIPS chips (older Indys, Indigo2s, etc).
# CFLAGS = -fullwarn -n32 -mips3 -Ofast -OPT:Olimit=0 -IPA

# PlayStation2 Linux
# CFLAGS = -O2 -mcpu=r5900 -fsingle-precision-constant -fstrength-reduce \
#     -fomit-frame-pointer -ffast-math -fsigned-char -pipe -malign-loops=2 
#     -malign-jumps=2 -funroll-loops

ifneq (,$(findstring gcc,$(CC)))

  #########################################################################
  # Special cases
  #########################################################################

  # Uncomment for a Linux/PowerPC system.
  # CFLAGS += -fsigned-char -mlongcall

  # Uncomment for OpenStep.  This might also apply to some early versions 
  # of Mac OS X.
  # CFLAGS += -traditional-cpp


  #########################################################################
  # Warnings
  #########################################################################
  
  # Check for C89 + GNU extensions compliance.
  CFLAGS += -std=gnu89

  # Show all warnings.
  CFLAGS += -Wall

  # Don't warn about unused variables.
  CFLAGS += -Wno-unused

  # Warn about declarations after statements.
  # CFLAGS += -Wdeclaration-after-statement

  # Don't warn about code that might break strict aliasing rules. 
  # CFLAGS += -Wno-strict-aliasing


  #########################################################################
  # Debugging
  #########################################################################

  # Detect non-ANSI C code.
  # CFLAGS += -pedantic -ansi -D_XOPEN_SOURCE -D_BSD_SOURCE \
  # -Wno-long-long -Wno-trigraphs -Dasm=__asm__
 
  # Check for C89 compliance.
  # CFLAGS += -std=c89

  # Enable debugging (e.g., using gdb).
  # CFLAGS += -ggdb
 
  # Enable gprof profiling.
  # CFLAGS += -pg


  #########################################################################
  # General optimizations
  #########################################################################
  
  # Optimization level -- choose one of these.
  # Use -O1 if you suspect that -O2 is producing bad code said:**
> Linux powerhouse 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux 
[quote=output of fglrxinfo]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
[/quote] 
My video card is an ATI Radeon X300 based PCI-Express card with 256Mb video RAM, but I have not been able to get direct rendering to work so I avoided using it in this makefile.

---

