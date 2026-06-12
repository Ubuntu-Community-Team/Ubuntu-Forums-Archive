---
title: "Problem building outdated (0.61) dosbox from source"
date: 2006-06-21
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2006-06-21
Why would I want to, you ask?  Mechwarrior (the original) apparently only works properly in this one version of dosbox (crashes after every mission in later versions).  I downloaded the source archive, extracted it, ran ./configure, everything seemed to work fine, then when I tried to issue make...

```
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetSize(Bit16u)’:
../../include/dos_inc.h:253: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::next_seg’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_PSP::GetSize()’:
../../include/dos_inc.h:254: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::next_seg’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetDTA(RealPt)’:
../../include/dos_inc.h:255: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::dta’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘RealPt DOS_PSP::GetDTA()’:
../../include/dos_inc.h:256: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::dta’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetEnvironment(Bit16u)’:
../../include/dos_inc.h:257: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::environment’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_PSP::GetEnvironment()’:
../../include/dos_inc.h:258: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::environment’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetParent(Bit16u)’:
../../include/dos_inc.h:262: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::psp_parent’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_PSP::GetParent()’:
../../include/dos_inc.h:263: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::psp_parent’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetStack(RealPt)’:
../../include/dos_inc.h:264: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::stack’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘RealPt DOS_PSP::GetStack()’:
../../include/dos_inc.h:265: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::stack’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘void DOS_PSP::SetInt22(RealPt)’:
../../include/dos_inc.h:266: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::int_22’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘RealPt DOS_PSP::GetInt22()’:
../../include/dos_inc.h:267: error: cannot bind packed field ‘0u->DOS_PSP::sPSP::int_22’ to ‘Bit32u&’
../../include/dos_inc.h: In member function ‘void DOS_DTA::SetDirID(Bit16u)’:
../../include/dos_inc.h:384: error: cannot bind packed field ‘0u->DOS_DTA::sDTA::dirID’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_DTA::GetDirID()’:
../../include/dos_inc.h:385: error: cannot bind packed field ‘0u->DOS_DTA::sDTA::dirID’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘void DOS_MCB::SetType(Bit8u)’:
../../include/dos_inc.h:457: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::type’ to ‘Bit8u&’
../../include/dos_inc.h: In member function ‘void DOS_MCB::SetSize(Bit16u)’:
../../include/dos_inc.h:458: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::size’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘void DOS_MCB::SetPSPSeg(Bit16u)’:
../../include/dos_inc.h:459: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::psp_segment’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit8u DOS_MCB::GetType()’:
../../include/dos_inc.h:460: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::type’ to ‘Bit8u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_MCB::GetSize()’:
../../include/dos_inc.h:461: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::size’ to ‘Bit16u&’
../../include/dos_inc.h: In member function ‘Bit16u DOS_MCB::GetPSPSeg()’:
../../include/dos_inc.h:462: error: cannot bind packed field ‘0u->DOS_MCB::sMCB::psp_segment’ to ‘Bit16u&’
make[3]: *** [debug.o] Error 1
make[3]: Leaving directory `/home/keithjr/dosbox/dosbox-0.61/src/debug'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keithjr/dosbox/dosbox-0.61/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keithjr/dosbox/dosbox-0.61'
make: *** [all] Error 2
```


What in the world is going on here?  Is this a problem with outdated code?  I can't figure out what could be wrong with my system to cause this.  I have build-essential, as well as several other packages recommended [here.]("http://www.ubuntuforums.org/showpost.php?p=923773&postcount=9")

Anybody have any ideas?

Sorry, I've posted three threads in the past three days... it's just that I've tried running three awesome games in linux for the first time (mechwarrior 2, dungeon keeper, and now mechwarrior) and have run into insurmountable brick walls for the past two.  I'm NOT letting this one slip through my fingers! :mad:

---

### Post by arizonagroovejet on 2006-06-22
Did you read the output of ./configure all the way through? 
In the past I've had stuff where the configure procses runs all the way through without dumping out with an error but when I do make I get errors. Reading through the output of ./configure has then revealed that it failed to find some libary but just said can't fid this' then carried on anyway, and you know how fast that ./configure output can fly up the screen.

---

### Post by keithjr on 2006-06-22
hmmm I did take a quick look through it but I figured anything obviously wrong would catch my eye.  Perhaps not!  I will look back over it when I get back to my room.

thanks!

/edit:  Okay, here it is, the output from ./configure

```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for egrep... grep -E
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
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking if environ can be included... no
checking if environ can be linked... yes
checking if compiler allows __attribute__... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
checking whether byte ordering is bigendian... no
checking for target cpu type... x86 compatible
checking whether x86 dynamic cpu core will be enabled... yes
checking whether fpu emulation will be enabled... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_check_sig in -lpng... yes
checking SDL/SDL_net.h usability... yes
checking SDL/SDL_net.h presence... yes
checking for SDL/SDL_net.h... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for main in -lGL... yes
checking for main in -lopengl32... no
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
checking whether opengl display output will be enabled... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/cpu/Makefile
config.status: creating src/cpu/core_full/Makefile
config.status: creating src/cpu/core_normal/Makefile
config.status: creating src/cpu/core_dyn_x86/Makefile
config.status: creating src/debug/Makefile
config.status: creating src/dos/Makefile
config.status: creating src/fpu/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/hardware/Makefile
config.status: creating src/ints/Makefile
config.status: creating src/misc/Makefile
config.status: creating src/shell/Makefile
config.status: creating src/platform/Makefile
config.status: creating src/platform/visualc/Makefile
config.status: creating visualc/Makefile
config.status: creating visualc_net/Makefile
config.status: creating include/Makefile
config.status: creating docs/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

I can't see anything wrong except the "no" results in the opengl lines.  I can't for the life of me figure out which package it wants me to have, though.  Any suggestions?  There is no package called lopengl32

---

### Post by keithjr on 2006-06-22
Well, I've been all up and down google, this form and several others, and have found no manifestations of this error except for myself.  Investigation proved pointless thanks to the ambiguous nature of the error message.  All I can chalk it up to is, perhaps, poor/incompatible code.  

Linux just isn't for gaming.  New or old.

---

### Post by keithjr on 2006-06-24
well one more question then I'll give up my mechwarrior efforts for good, I suppose....

Did dosbox 0.61 have different dependencies than the current dos box version?  It could be missing some library that perhaps isn't installed by apt-get for the recent versions (0.61 is fairly old).

Anybody know?

---

