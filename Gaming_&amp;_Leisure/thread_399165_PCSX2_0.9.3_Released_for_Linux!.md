---
title: "PCSX2 0.9.3 Released for Linux!"
date: 2007-04-02
forum: Gaming &amp; Leisure
---

### Post by buttons on 2007-04-02
Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").

I'm running Edgy, and I managed to compile the SVN, so here is a mini-howto for compilation.  This is by no means comprehensive, as who knows what -dev packages you might be missing that I've picked up somewhere along the line.

I KNOW it requires:

libbz2-dev
subversion
libjpeg62-dev
build-essential
libgtk2.0-dev
libxxf86vm-dev
x11proto-xf86vidmode-dev
automake1.9
Nvidia Cg-Toolkit (available [HERE]("http://developer.nvidia.com/object/cg_toolkit.html"))

The automake version is important, as it will spit all sorts of errors if you have an earlier version.

It PROBABLY requires:
libglu1-mesa-dev

I can't actually say it needs that for certain, only that I have it and the INSTALL file says you need OpenGL libs in order to compile.

-----------

Okay, so let's grab our required things:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```
Our maybe required things:
```
sudo apt-get install libglu1-mesa-dev
```

The SVN code:

```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```

Aaaand build it!

```
cd pcsx2
sh build.sh all
```

And hopefully everything should build!

EDIT: libbz2-dev is required for the ISO plugins to compile

---

### Post by hikaricore on 2007-04-02
Woot!

---

### Post by po0f on 2007-04-02
buttons,

This is wonderful news!  Btw, any reason you are trying to compile it from source?  I took the following steps to install it:

[list]
[*]extract contents to ~/.pcsx2
[*]create a startup file called "pcsx2" with the contents:
```
#!/bin/bash
cd ~/.pcsx2
LD_LIBRARY_PATH="./" ./pcsx2
```
You can put this in /usr/local/bin, just make sure it's executable (`chmod +x /usr/local/bin/pcsx2`)
[*]execute with `pcsx2` from the terminal
[*]look at the GUI (I don't own a PS2 so I don't have a BIOS)
[/list]

Now, I just need to get a PS2.  :)

---

### Post by buttons on 2007-04-02
Yes, I had to compile it from source.   Unfortunately every time I tried to run the 32-bit binary I got a mysterious "Floating Point Exception" error :(

As per my original post, though, compiling from source worked finally!

NOTE: If you have a dual core proc, go into Configure->CPU and check everything.  It's gonna make a HUGE difference.

---

### Post by po0f on 2007-04-02
buttons,

Are you running a 64-bit install?  There is a 64-bit binary available.  :)

[EDIT]

I'm not trying to hassle you or anything, I was just wondering.

---

### Post by buttons on 2007-04-02
No.  Despite having a 64-bit processor I don't run the 64-bit version of ubuntu.  In the future, though, pcsx2-64 will be much faster than pcsx2-32 and I'll probably make the switch for that reason.

---

### Post by hikaricore on 2007-04-02
Nearly went mad before I realized that I didn't have automake installed anymore.  >.<

Ty buttons.  :)

---

### Post by plb on 2007-04-02
Can anyone setup a repository for this, svn gives me a whole bunch of errors while building it atm? Also, what's the gameplay like on this thing? Is it worth installing right now?

---

### Post by Fator dee on 2007-04-02
I wouldn't compile from svn, because it might not be as stable as the code for 0.9.3. or it couldn't even compile at all.

And to compile you also need libjpeg62-dev, if buttons could add it to the list.

---

### Post by plb on 2007-04-02
> **Fator dee said:**
> I wouldn't compile from svn, because it might not be as stable as the code for 0.9.3. or it couldn't even compile at all.

And to compile you also need libjpeg62-dev, if buttons could add it to the list.

I take it you have tried it? How does it play?

---

### Post by justin whitaker on 2007-04-02
Any idea which games work? I don't have any ROMs, but if, say, the Final Fantasy series worked, I might pop down to the local GameStop and pick up a used disc. Keep it legal people! :)

---

### Post by buttons on 2007-04-02
> **justin whitaker said:**
> Any idea which games work? I don't have any ROMs, but if, say, the Final Fantasy series worked, I might pop down to the local GameStop and pick up a used disc. Keep it legal people! :)

The full compatibility list is located [here]("http://www.pcsx2.net/compat.php?c=key").

It's funny you should ask about the FF series specifically, as FFX is something of a killer app for this emulator.  You can check out the compatibility status of the FF games [here]("http://www.pcsx2.net/compat.php?&c=f&s1=1&s2=1&s3=1&s4=1&s5=1&p=2") and the pages following.

Before you run out and spend your hard-earned cash, though, I would test on other playable games (if you have access to them) in order to determine if your system is powerful enough.  Basically a dual core system is required, and a very fast dual core system is preferred.  YMMV, as always.

---

### Post by justin whitaker on 2007-04-02
> **buttons said:**
> The full compatibility list is located [here]("http://www.pcsx2.net/compat.php?c=key").

It's funny you should ask about the FF series specifically, as FFX is something of a killer app for this emulator.  You can check out the compatibility status of the FF games [here]("http://www.pcsx2.net/compat.php?&c=f&s1=1&s2=1&s3=1&s4=1&s5=1&p=2") and the pages following.

Before you run out and spend your hard-earned cash, though, I would test on other playable games (if you have access to them) in order to determine if your system is powerful enough.  Basically a dual core system is required, and a very fast dual core system is preferred.  YMMV, as always.

Hmmm, no dual core here. AMD64. :( I'll check the specs and such after work, since websense has the site blocked.

---

### Post by plb on 2007-04-02
Can't seem to play any games........screen pops up and closes

        F1 - save state
        (Shift +) F2 - cycle states
        F3 - load state
        F10 - dump performance counters
        F11 - save GS state
        F12 - dump hardware registers
PCSX2 v0.9.3 save ver: 7a30000e
EE pc offset: 0x2a8, PSX pc offset: 0x208
x86Init: 
        CPU vender name =  AuthenticAMD
        FamilyID        =  0
        x86Family =  AMD Athlon(tm) 64 Processor 3300+
        CPU speed =  1.810 Ghz
        x86PType  =  Standard OEM
        x86Flags  =  078bfbff
        x86EFlags =  e1d3fbff
Features: 
        Detected MMX
        Detected SSE
        Detected SSE2
        Not Detected SSE3
 Extented AMD Features: 
        Detected MMX2
        Detected 3DNOW
        Detected 3DNOW2
EE Recompiler data reset
Bios Version 1.60



**************
rom1 NOT FOUND
**************





**************
rom2 NOT FOUND
**************





**************
erom NOT FOUND
**************


GIF reset
NTSC
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: *********
ZeroGS: OGL WARNING: multiple render targets not supported, some effects might look bad
ZeroGS: *********
Segmentation fault
plb@plb-desktop:~/pcsx2/bin$

---

### Post by buttons on 2007-04-02
Interesting opengl errors there.  I assume you have direct rendering available?  What card/drivers?

If this doesn't turn out to be something simple I would echo your report on the [official forums]("http://forums.ngemu.com/pcsx2-official-forum/87616-pcsx2-0-93-bug-reports.html").

---

### Post by plb on 2007-04-02
> **buttons said:**
> Interesting opengl errors there.  I assume you have direct rendering available?  What card/drivers?

If this doesn't turn out to be something simple I would echo your report on the [official forums]("http://forums.ngemu.com/pcsx2-official-forum/87616-pcsx2-0-93-bug-reports.html").

nvidia geforce fx 5200

---

### Post by PhatStreet on 2007-04-02
Is a really powerful graphics card needed? I have a pretty fast dual-core system and the only thing really holding it back is the graphics card. I tried just booting to the BIOS and I didn't even get 4 FPS on the cubes animation.

---

### Post by buttons on 2007-04-02
> **plb said:**
> nvidia geforce fx 5200

Which driver version are you using?  Do you have direct rendering enabled?

---

### Post by buttons on 2007-04-02
> **PhatStreet said:**
> Is a really powerful graphics card needed? I have a pretty fast dual-core system and the only thing really holding it back is the graphics card. I tried just booting to the BIOS and I didn't even get 4 FPS on the cubes animation.

Under the configuration menu click CPU and check everything.

EErec
VU0rec
VU1rec
MTGS
DC

Normal frame skip.

That should allow you to use your CPU to its fullest.  
The answer to your question is (for the most part) no.  The emulator is almost entirely CPU-limited.  There are some games, notably FF12 and others, that can benefit from a more powerful GPU.

---

### Post by plb on 2007-04-02
> **buttons said:**
> Which driver version are you using?  Do you have direct rendering enabled?

latest nvidia and yes I have direct rendering enabled...that seems to be just a warning.

---

### Post by BoyOfDestiny on 2007-04-02
Very cool.  

At least I'll have the option of playing my games if my sis takes the ps2 to her dorm...

:guitar:

---

### Post by leech on 2007-04-02
I just want to know if I can play Baldur's Gate Dark Alliance with it.  :D  My brother has the game on his PS2 and it rocks, but of course I'd rather play it on my own PC rather than have to try and get some game time on his system.

Leech

---

### Post by Fator dee on 2007-04-03
> **plb said:**
> I take it you have tried it? How does it play?

Compiled fine and works fine, though I don't have any games atm to test it, I'll be back after I've borrowed FFX from my friend.

---

### Post by hikaricore on 2007-04-03
> **Fator dee said:**
> Compiled fine and works fine, though I don't have any games atm to test it, I'll be back after I've borrowed FFX from my friend.

FFX runs very well, although it may be a bit slow unless your system is a beast. :)

I only got about 20fps or so >.<

---

### Post by Rooy on 2007-04-04
How did you install the Cg kit? I did

$> cd / && sudo tar xvf ~/Cg-1.5_x86_64.tar.gz

and things looked like they went in proper places.

$> ls /usr/include/Cg/
cg_bindlocations.h  cg_enums.h   cgGL.h           cg.h
cg_datatypes.h      cg_errors.h  cgGL_profiles.h  cg_profiles.h

But when I ran ./configure manually in pcsx2/plugins/gs/zerogs/opengl there's a line:

checking Cg... checking for main in -ljpeg... yes

which made me think that the Cg kit was not picked up by the configure script.

When I run pcsx2 without any disc in DVD drive, the screen is black. Is this normal?

---

### Post by buttons on 2007-04-04
> **Rooy said:**
> How did you install the Cg kit? I did

$> cd / && sudo tar xvf ~/Cg-1.5_x86_64.tar.gz

and things looked like they went in proper places.

$> ls /usr/include/Cg/
cg_bindlocations.h  cg_enums.h   cgGL.h           cg.h
cg_datatypes.h      cg_errors.h  cgGL_profiles.h  cg_profiles.h

But when I ran ./configure manually in pcsx2/plugins/gs/zerogs/opengl there's a line:

checking Cg... checking for main in -ljpeg... yes

which made me think that the Cg kit was not picked up by the configure script.

When I run pcsx2 without any disc in DVD drive, the screen is black. Is this normal?

I downloaded the rpm and used alien to install Cg :oops:

When you run pcsx2 without any disk in the drive, the BIOS should be run.  If you've ever seen a PS2 operate without a disk in the drive, it makes kind of a cube thing with some lights revolving around it, then gives you some memory card options, etc.  If you aren't seeing anything there may be a problem with your BIOS, or it may in fact be going so slowly you haven't seen any frames rendered yet.  You DO in fact have a PS2 bios in your PCSX2ROOT/bin/bios directory, don't you?

---

### Post by Duffman2010 on 2007-04-04
I installed Cg the same way and it worked. If pcsx2 were really not finding Cg includes it wouldn't compile. It would throw errors complaining about that. It seems that your problem has another cause.

---

### Post by plb on 2007-04-04
For some reason I cannot fix this problem. I put a ps2 disc in the drive and I click run cd and the a screen pops up then I get a segfault. I tried installing via svn and also the 0.9.3 release. Does anyone else get this?

---

### Post by buttons on 2007-04-04
> **plb said:**
> For some reason I cannot fix this problem. I put a ps2 disc in the drive and I click run cd and the a screen pops up then I get a segfault. I tried installing via svn and also the 0.9.3 release. Does anyone else get this?

Please post this in the [Official Forums]("http://forums.ngemu.com/pcsx2-official-forum/87616-pcsx2-0-93-bug-reports.html").

It's very likely the developers will ask you to compile a debug version and use gdb to do a backtrace on the fault.

---

### Post by buttons on 2007-04-04
> **plb said:**
> Can't seem to play any games........screen pops up and closes

        F1 - save state
        (Shift +) F2 - cycle states
        F3 - load state
        F10 - dump performance counters
        F11 - save GS state
        F12 - dump hardware registers
PCSX2 v0.9.3 save ver: 7a30000e
EE pc offset: 0x2a8, PSX pc offset: 0x208
x86Init: 
        CPU vender name =  AuthenticAMD
        FamilyID        =  0
        x86Family =  AMD Athlon(tm) 64 Processor 3300+
        CPU speed =  1.810 Ghz
        x86PType  =  Standard OEM
        x86Flags  =  078bfbff
        x86EFlags =  e1d3fbff
Features: 
        Detected MMX
        Detected SSE
        Detected SSE2
        Not Detected SSE3
 Extented AMD Features: 
        Detected MMX2
        Detected 3DNOW
        Detected 3DNOW2
EE Recompiler data reset
Bios Version 1.60



**************
rom1 NOT FOUND
**************





**************
rom2 NOT FOUND
**************





**************
erom NOT FOUND
**************


GIF reset
NTSC
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: *********
ZeroGS: OGL WARNING: multiple render targets not supported, some effects might look bad
ZeroGS: *********
Segmentation fault
plb@plb-desktop:~/pcsx2/bin$

Actually, someone with a very similar bug just posted a trace on the forums.  Apparently the program was attempting to draw ARB visuals without asking the card if it supported it.  The current SVN should fix this.

---

### Post by plb on 2007-04-04
alright, I'll try downloading latest svn and rebuliding...I'll post back if it works out.

---

### Post by plb on 2007-04-04
Ok svn solved one problem now I get error opening gs plugin ZeroGS: *********

---

### Post by buttons on 2007-04-06
I discovered my ISO plugins weren't compiling (without any errors in the build.sh all), and apparently the reason is I didn't have libbz2-dev installed.  I honestly didn't know I *should* have had them until this morning.

Either way the original post is updated.

---

### Post by boyprodigy on 2007-04-08
I was wondering if someone could help me out. I get the following when trying to build it. I'm still new to linux and compiling things is kind of beyond me at this point. Although, I'm not stupid as I did do extensive java programing in my younger years 


```

----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
In file included from GSmain.cpp:39:
zerogs.h:36:19: error: Cg/cg.h: No such file or directory
zerogs.h:37:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:119: error: ‘CGprogram’ does not name a type
zerogs.h:127: error: ‘CGprogram’ does not name a type
zerogs.h:128: error: ‘CGparameter’ does not name a type
zerogs.h:129: error: ‘CGparameter’ does not name a type
zerogs.h:130: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:140: error: ‘CGprogram’ does not name a type
zerogs.h:141: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:171: error: ‘CGparameter’ does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
jon@Midgar:~/pcsx2$ 

```

---

### Post by buttons on 2007-04-08
You're missing the [Cg Toolkit]("http://developer.nvidia.com/object/cg_toolkit.html") from nVidia.

Easiest way to install it is to grab [this RPM]("http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007.i386.rpm") (32-bit) and then do the following in whatever directory you downloaded it into:
```
sudo apt-get install alien
alien Cg-1.5_Feb2007.i386.rpm
sudo dpkg -i Cg-1.5_Feb2007.i386.deb
```

Then start your sh build.sh all again.

---

### Post by boyprodigy on 2007-04-08
Thanks for the quick response buttons! 

Now I'm having another problem :( . When I try to run it the following pops up

```
jon@Midgar:~/pcsx2/bin$ ./pcsx2

*** stack smashing detected ***: ./pcsx2 terminated
Aborted (core dumped)
jon@Midgar:~/pcsx2/bin$ 

```

Any idea on what the problem might be?

---

### Post by buttons on 2007-04-08
> **boyprodigy said:**
> Thanks for the quick response buttons! 

Now I'm having another problem :( . When I try to run it the following pops up

```
jon@Midgar:~/pcsx2/bin$ ./pcsx2

*** stack smashing detected ***: ./pcsx2 terminated
Aborted (core dumped)
jon@Midgar:~/pcsx2/bin$ 

```

Any idea on what the problem might be?

Let me guess...you've put a bios in the <root>/bin/bios directory, which is v2.00 or later?  For one reason or another there are some later PS2 BIOSs that bork pcsx2.  I'm kinda glad you have this problem (if that is indeed the reason you're experiencing this error), because I've posted it all over the official forums and apparently no one else has the issue.

My suggestion is to use a valid PS2 BIOS v1.60 or earlier, and make sure the offending ones are not in the bios directory, or your stacks will continue smushing.

---

### Post by boyprodigy on 2007-04-08
And Mr buttons does it again :guitar: 

it was the bios, I put in a 1.6 and it working super fine. I think I'll try putting Ubuntu 64bit on my PC and trying it out with that too. 

Thank you very much for your help buttons!

---

### Post by buttons on 2007-04-08
> **boyprodigy said:**
> And Mr buttons does it again :guitar: 

it was the bios, I put in a 1.6 and it working super fine. I think I'll try putting Ubuntu 64bit on my PC and trying it out with that too. 

Thank you very much for your help buttons!

:D

---

### Post by The Noble on 2007-04-08
I just wanted to point out the "requirements" for running pcsx2. Basically, you need a beast of a computer ***In Windows***, so the same stands for linux. The two major specs needed are the cpu and gpu. The cpu should be at least dual core (or extremely oc'ed) to even bother, while the gpu should be as powerful as the nvidia 6600 to even consider trying a 3d game. A gig of ram is recommended, but 512 is feasable. I would also like to point out that FFX is currently the most playable game in both speed and comptibility, so if you own it and a reasonably powerful computer, you should be able to play it full speed all the way through.

---

### Post by damvcoool on 2007-04-08
can anyone build a deb package of this emulator :D

---

### Post by Drezliok on 2007-04-08
> **damvcoool said:**
> can anyone build a deb package of this emulator :D

Nice but I'd settle for a a good set of instructions, I might reread the whole thread and make some up if it works I'll post it.

---

### Post by darkteckno on 2007-04-11
that would be great

---

### Post by plb on 2007-04-11
I got it to build but apparently my graphics card isn't up to par with their specs. According to someone on their IRC channel you need at least a fx5900 for it to work while I'm stuck with a 5200. Of course that is just what I was told.

---

### Post by jollyr0ger on 2007-04-14
Hi to all!

I've compiled succesfully from SVN, then pcsx2 works.
but when i start the emulation (File / Run CD) the screen of ZeroGS returns me "error opening GS plugin" and stop working.

the same problem on the official forum is here:
[http://forums.ngemu.com/pcsx2-official-forum/88156-error-openin-gs-plugin.html](http://forums.ngemu.com/pcsx2-official-forum/88156-error-openin-gs-plugin.html)
but there's no solution in those pages.

you have any suggestion?

*tnx

---

### Post by plb on 2007-04-14
> **jollyr0ger said:**
> Hi to all!

I've compiled succesfully from SVN, then pcsx2 works.
but when i start the emulation (File / Run CD) the screen of ZeroGS returns me "error opening GS plugin" and stop working.

the same problem on the official forum is here:
[http://forums.ngemu.com/pcsx2-official-forum/88156-error-openin-gs-plugin.html](http://forums.ngemu.com/pcsx2-official-forum/88156-error-openin-gs-plugin.html)
but there's no solution in those pages.

you have any suggestion?

*tnx

That is the error I got. They said my video card wasn't good enough. I'm not sure if the guy was a dev or just some random person.

---

### Post by ura_renge on 2007-04-21
when compiling it gives error me.

```
Building PeopsSPU2
------------------
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  alsa.c
alsa.c:40:28: error: alsa/asoundlib.h: No existe el fichero ó directorio
alsa.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alsa.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buffer_size’
alsa.c: In function ‘SetupSound’:
alsa.c:68: error: ‘snd_pcm_hw_params_t’ undeclared (first use in this function)
alsa.c:68: error: (Each undeclared identifier is reported only once
alsa.c:68: error: for each function it appears in.)
alsa.c:68: error: ‘hwparams’ undeclared (first use in this function)
alsa.c:69: error: ‘snd_pcm_sw_params_t’ undeclared (first use in this function)
alsa.c:69: error: ‘swparams’ undeclared (first use in this function)
alsa.c:70: error: ‘snd_pcm_status_t’ undeclared (first use in this function)
alsa.c:70: error: ‘status’ undeclared (first use in this function)
alsa.c:82: error: ‘SND_PCM_FORMAT_S16_LE’ undeclared (first use in this function)
alsa.c:86: warning: implicit declaration of function ‘snd_pcm_open’
alsa.c:86: error: ‘handle’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_STREAM_PLAYBACK’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_NONBLOCK’ undeclared (first use in this function)
alsa.c:89: warning: implicit declaration of function ‘snd_strerror’
alsa.c:89: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:93: warning: implicit declaration of function ‘snd_pcm_nonblock’
alsa.c:95: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:99: warning: implicit declaration of function ‘snd_pcm_hw_params_alloca’
alsa.c:100: warning: implicit declaration of function ‘snd_pcm_sw_params_alloca’
alsa.c:101: warning: implicit declaration of function ‘snd_pcm_hw_params_any’
alsa.c:103: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:107: warning: implicit declaration of function ‘snd_pcm_hw_params_set_access’
alsa.c:107: error: ‘SND_PCM_ACCESS_RW_INTERLEAVED’ undeclared (first use in this function)
alsa.c:109: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:113: warning: implicit declaration of function ‘snd_pcm_hw_params_set_format’
alsa.c:115: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:119: warning: implicit declaration of function ‘snd_pcm_hw_params_set_channels’
alsa.c:121: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:125: warning: implicit declaration of function ‘snd_pcm_hw_params_set_rate_near’
alsa.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:131: warning: implicit declaration of function ‘snd_pcm_hw_params_set_buffer_time_near’
alsa.c:133: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:137: warning: implicit declaration of function ‘snd_pcm_hw_params_set_period_time_near’
alsa.c:139: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:143: warning: implicit declaration of function ‘snd_pcm_hw_params’
alsa.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:149: warning: implicit declaration of function ‘snd_pcm_status_alloca’
alsa.c:150: warning: implicit declaration of function ‘snd_pcm_status’
alsa.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:156: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c:156: warning: implicit declaration of function ‘snd_pcm_status_get_avail’
alsa.c: In function ‘RemoveSound’:
alsa.c:165: error: ‘handle’ undeclared (first use in this function)
alsa.c:167: warning: implicit declaration of function ‘snd_pcm_drop’
alsa.c:168: warning: implicit declaration of function ‘snd_pcm_close’
alsa.c: In function ‘SoundGetBytesBuffered’:
alsa.c:181: error: ‘handle’ undeclared (first use in this function)
alsa.c:183: warning: implicit declaration of function ‘snd_pcm_avail_update’
alsa.c:185: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c: In function ‘SoundFeedVoiceData’:
alsa.c:198: error: ‘handle’ undeclared (first use in this function)
alsa.c:200: warning: implicit declaration of function ‘snd_pcm_state’
alsa.c:200: error: ‘SND_PCM_STATE_XRUN’ undeclared (first use in this function)
alsa.c:201: warning: implicit declaration of function ‘snd_pcm_prepare’
alsa.c:202: warning: implicit declaration of function ‘snd_pcm_writei’
make: *** [alsa.o] Error 1
Error with building plugins
```

as I solve it?? 



----------
Sorry by my English, I speak Spanish

---

### Post by buttons on 2007-04-21
> **ura_renge said:**
> when compiling it gives error me.

```
Building PeopsSPU2
------------------
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  alsa.c
alsa.c:40:28: error: alsa/asoundlib.h: No existe el fichero ó directorio
alsa.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alsa.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buffer_size’
alsa.c: In function ‘SetupSound’:
alsa.c:68: error: ‘snd_pcm_hw_params_t’ undeclared (first use in this function)
alsa.c:68: error: (Each undeclared identifier is reported only once
alsa.c:68: error: for each function it appears in.)
alsa.c:68: error: ‘hwparams’ undeclared (first use in this function)
alsa.c:69: error: ‘snd_pcm_sw_params_t’ undeclared (first use in this function)
alsa.c:69: error: ‘swparams’ undeclared (first use in this function)
alsa.c:70: error: ‘snd_pcm_status_t’ undeclared (first use in this function)
alsa.c:70: error: ‘status’ undeclared (first use in this function)
alsa.c:82: error: ‘SND_PCM_FORMAT_S16_LE’ undeclared (first use in this function)
alsa.c:86: warning: implicit declaration of function ‘snd_pcm_open’
alsa.c:86: error: ‘handle’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_STREAM_PLAYBACK’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_NONBLOCK’ undeclared (first use in this function)
alsa.c:89: warning: implicit declaration of function ‘snd_strerror’
alsa.c:89: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:93: warning: implicit declaration of function ‘snd_pcm_nonblock’
alsa.c:95: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:99: warning: implicit declaration of function ‘snd_pcm_hw_params_alloca’
alsa.c:100: warning: implicit declaration of function ‘snd_pcm_sw_params_alloca’
alsa.c:101: warning: implicit declaration of function ‘snd_pcm_hw_params_any’
alsa.c:103: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:107: warning: implicit declaration of function ‘snd_pcm_hw_params_set_access’
alsa.c:107: error: ‘SND_PCM_ACCESS_RW_INTERLEAVED’ undeclared (first use in this function)
alsa.c:109: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:113: warning: implicit declaration of function ‘snd_pcm_hw_params_set_format’
alsa.c:115: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:119: warning: implicit declaration of function ‘snd_pcm_hw_params_set_channels’
alsa.c:121: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:125: warning: implicit declaration of function ‘snd_pcm_hw_params_set_rate_near’
alsa.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:131: warning: implicit declaration of function ‘snd_pcm_hw_params_set_buffer_time_near’
alsa.c:133: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:137: warning: implicit declaration of function ‘snd_pcm_hw_params_set_period_time_near’
alsa.c:139: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:143: warning: implicit declaration of function ‘snd_pcm_hw_params’
alsa.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:149: warning: implicit declaration of function ‘snd_pcm_status_alloca’
alsa.c:150: warning: implicit declaration of function ‘snd_pcm_status’
alsa.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:156: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c:156: warning: implicit declaration of function ‘snd_pcm_status_get_avail’
alsa.c: In function ‘RemoveSound’:
alsa.c:165: error: ‘handle’ undeclared (first use in this function)
alsa.c:167: warning: implicit declaration of function ‘snd_pcm_drop’
alsa.c:168: warning: implicit declaration of function ‘snd_pcm_close’
alsa.c: In function ‘SoundGetBytesBuffered’:
alsa.c:181: error: ‘handle’ undeclared (first use in this function)
alsa.c:183: warning: implicit declaration of function ‘snd_pcm_avail_update’
alsa.c:185: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c: In function ‘SoundFeedVoiceData’:
alsa.c:198: error: ‘handle’ undeclared (first use in this function)
alsa.c:200: warning: implicit declaration of function ‘snd_pcm_state’
alsa.c:200: error: ‘SND_PCM_STATE_XRUN’ undeclared (first use in this function)
alsa.c:201: warning: implicit declaration of function ‘snd_pcm_prepare’
alsa.c:202: warning: implicit declaration of function ‘snd_pcm_writei’
make: *** [alsa.o] Error 1
Error with building plugins
```

as I solve it?? 



----------
Sorry by my English, I speak Spanish

Try ```
sudo apt-get install libasound2-dev
``` and recompiling.

---

### Post by KamiCrazy on 2007-04-24
I have compiled a 64 bit version and attempted to run the bios (no games)

all bios' I tried crash upon run giving me illegal instruction errors. Turning off the emotion engine recompiler allows me to run the bios but then I get really horrible frame rates <10. the V0 V1 recompilers are fine though I can have them switched on/off no problem.

Not sure what the heck is wrong with my machine if I can't run the bios with the EE recompiler on, its supposed to be extremely compatible.

---

### Post by Agret on 2007-04-28
Thanks for the guide, helped me out :)

---

### Post by deimios on 2007-05-01
Great guide. Thumbs up.
Got PCSX2 up and running on Kubuntu Feisty. (Only problem was the asound-dev problem)
I started up Disgaea 2 and it worked... well mostly. The sound and emulation is almost perfect. Only that after the startup logos the screen remains black... but the game runs.
Probably because I disabled SSE2.

Guess it's back to windows for playing disgaea... :((

---

### Post by salem1234 on 2007-05-04
can anyone make an video:popcorn:  for how to bulid the svn

becuse im dummy:confused:  cant do anything by myself and icant undrstand the english 

so can anyone make video:popcorn:  plz

and can any one post pic inthe fourm

---

### Post by KaridaSerious on 2007-05-10
ZeroGS: Disabling MRT depth writing
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
Illegal instruction (core dumped)

Happens when i try run DBZ Budokai 3. What does that mean. Black screen appears about 5 sek and then crashes.

---

### Post by buttons on 2007-05-10
Steps to file a bug report:

[LIST=1]
[*]Make an account on the [Official Forum]("http://forums.ngemu.com/pcsx2-official-forum/")
[*]Open build.sh (from SVN), and add --enable-debug to PCSX2OPTIONS
[*]Compile your version of PCSX2 from SVN using sh build.sh all
[*]```
sudo apt-get install gdb
``` (if you don't already have it)
[*]```
gdb /path/to/pcsx2
```
[*]```
run
``` at the gdb command line
[*]Make a post on the forums with a clear title (ie DBZ 3 crashes on 0.9.3 from SVN, linux).  Be sure to put in all of your system specs, and the crash trace from gdb.
[*]Let the devs take it from there.
[/LIST]

---

### Post by robgig1088 on 2007-05-30
I needed asound-dev to compile the sound plugin.  Make sure you have it installed.  Other than that, works great!

---

### Post by CM Xtasy on 2007-05-31
```
In file included from GSmain.cpp:39:
zerogs.h:36:19: error: Cg/cg.h: No such file or directory
zerogs.h:37:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:119: error: ‘CGprogram’ does not name a type
zerogs.h:127: error: ‘CGprogram’ does not name a type
zerogs.h:128: error: ‘CGparameter’ does not name a type
zerogs.h:129: error: ‘CGparameter’ does not name a type
zerogs.h:130: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:140: error: ‘CGprogram’ does not name a type
zerogs.h:141: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:171: error: ‘CGparameter’ does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/chris/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins

```

Help? :(

---

### Post by buttons on 2007-06-01
> **CM Xtasy said:**
> ```
In file included from GSmain.cpp:39:
zerogs.h:36:19: error: Cg/cg.h: No such file or directory
zerogs.h:37:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:119: error: ‘CGprogram’ does not name a type
zerogs.h:127: error: ‘CGprogram’ does not name a type
zerogs.h:128: error: ‘CGparameter’ does not name a type
zerogs.h:129: error: ‘CGparameter’ does not name a type
zerogs.h:130: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:140: error: ‘CGprogram’ does not name a type
zerogs.h:141: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:171: error: ‘CGparameter’ does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/chris/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins

```

Help? :(

Install the CG toolkit from nvidia.

---

### Post by cleverselfreferentialname on 2007-06-07
Huh. Whenever I try to do ANYTHING under this thing, it segfaults. I really think that people should release no software for Linux at all rather than shitty software.

---

### Post by Sockerdrickan on 2007-06-08
It's not shitty because you don't know how to compile it.

---

### Post by BorjaRRR on 2007-06-12
When i run pcsx2 happens this :
> 
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.2
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: ******
ZeroGS: GS WARNING: Floating point render targets not supported, switching to 32bit
ZeroGS: *********
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32768
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36864
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40960
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45056
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32769
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36865
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40961
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45057
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32770
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36866
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40962
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45058
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32771
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36867
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40963
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45059
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing



ZeroGS window is black but fps continue counting
Any solution?
Sorry for my bad english ;)

---

### Post by Sikarian on 2007-06-12
Change of post


Got my segmentation fault fixed.  Now when I boot up the game (Shadow of the Collosus in this case)...It's a good 25-30 while displaying the sony logo and all that jazz.

When the game actually begins displaying 3d, I drop down to 1-2 fps and it grinds to a screeching halt.

I've tried disabling bi-linear filtering and that doesn't help any.  The sound also jutters a lot.


I'm running an Intel Core 2 duo T2700 @ 2.00GHZ, 1gb of DDR2 memory and a 128mb NVidia 7200 Go card.


Even going in the BIOS is slow and drops framerate.

---

### Post by Jimbob17 on 2007-06-12
> **Sikarian said:**
> Change of post


Got my segmentation fault fixed.  Now when I boot up the game (Shadow of the Collosus in this case)...It's a good 25-30 while displaying the sony logo and all that jazz.

When the game actually begins displaying 3d, I drop down to 1-2 fps and it grinds to a screeching halt.

I've tried disabling bi-linear filtering and that doesn't help any.  The sound also jutters a lot.


I'm running an Intel Core 2 duo T2700 @ 2.00GHZ, 1gb of DDR2 memory and a 128mb NVidia 7200 Go card.


Even going in the BIOS is slow and drops framerate.

I haven't done much testing with PCSX2, I need to compile my own version I think, but I think you're going to be limited by your graphics card. From what I can see, doing a quick Google search, the 7200 is a pretty basic graphics card.

Your dual core CPU should handle it nicely but the bottleneck is the graphics card.

---

### Post by Sikarian on 2007-06-12
I wouldn't really call a 7200 Go a pretty basic graphics card :(

I use this machine to play all manner of games, and it has absolutely no trouble pushing out the power necessary to run any game I've thrown at it so far.


That hut my feelings :cry:

---

### Post by The Noble on 2007-06-12
He is correct though. Certain games should run very well (Final Fantasy X) while others (MGS3 or RE4) will not even break 20 fps. Any game that is cpu dependent should run great for you. GPU dependent will die. Make sure your laptop does not overheat, at least.

---

### Post by Sikarian on 2007-06-12
Is there any particular reason that even going into the BIOS is slow?  You know, the 3d cubes and all that.  That's the same 2-4 fps I receive when loading up the game.

Any possibility of using a different display plugin that might help any?

---

### Post by buttons on 2007-06-12
> **Sikarian said:**
> Is there any particular reason that even going into the BIOS is slow?  You know, the 3d cubes and all that.  That's the same 2-4 fps I receive when loading up the game.

Any possibility of using a different display plugin that might help any?

Have you enabled all of the recompilers and the dual core stuff?

---

### Post by Sikarian on 2007-06-12
> **buttons said:**
> Have you enabled all of the recompilers and the dual core stuff?

I have.  There was a minuscule difference :(

---

### Post by The Noble on 2007-06-12
With a pentium 4 3.0 Ghz and an ATI x700 pro (in windows XP) I was getting around 40 fps with the bios and 25 fps in FFX. There is definitely a problem with your setup. You are using ZeroGS, right?

---

### Post by Sikarian on 2007-06-13
> **The Noble said:**
> With a pentium 4 3.0 Ghz and an ATI x700 pro (in windows XP) I was getting around 40 fps with the bios and 25 fps in FFX. There is definitely a problem with your setup. You are using ZeroGS, right?

Yeah, the plugins I'm using: 

**Graphics**: ZeroGS KOSMOS OpenGL 0.96.2
**Sound**: P.E.Op.S. SPU2 1.6.0
**First Controller**:  ZeroPAD 0.1.0
**Second Controller**: ZeroPAD 0.1.0
**Dev9**:  DEV9null Driver 0.3.0
**Cdvdrom**:  EFP polling CDVD Driver 0.4.0
**Usb**:  USBnull Driver 0.5.0
**FireWire**:  FWnull Driver 0.4.0


Graphics options, I've got no Anti-Aliasing, Bilinear Filtering off, 640x480 resolution.

CPU Config:  EERec - EE/IOP recompiler** ON**
  VU0rec - enable recompiler for VU0 unit  **ON**
  VU1rec - enable recompiler for VU1 unit** ON**

 Multi Threaded GS Mode  ** ON**
 Dual Core Mode **ON**

Frame limiting I've tired Normal, Frame Skip and VU Skip, no improvements.


I've noticed that the BIOS loading screen with the cubes is about 15-20.  After I get to the menus everything is fine.

Although trying to test the BIOS this morning leads me into another problem, I hit RUN CD or Execute (with no CD in drive) to try to bring BIOS up, and I get a black screen running at 250 FPS with nothing happening.  Nothing's changed since yesterday, so I have no idea.

---

### Post by buttons on 2007-06-17
> **Sikarian said:**
> Yeah, the plugins I'm using: 

**Graphics**: ZeroGS KOSMOS OpenGL 0.96.2
**Sound**: P.E.Op.S. SPU2 1.6.0
**First Controller**:  ZeroPAD 0.1.0
**Second Controller**: ZeroPAD 0.1.0
**Dev9**:  DEV9null Driver 0.3.0
**Cdvdrom**:  EFP polling CDVD Driver 0.4.0
**Usb**:  USBnull Driver 0.5.0
**FireWire**:  FWnull Driver 0.4.0


Graphics options, I've got no Anti-Aliasing, Bilinear Filtering off, 640x480 resolution.

CPU Config:  EERec - EE/IOP recompiler** ON**
  VU0rec - enable recompiler for VU0 unit  **ON**
  VU1rec - enable recompiler for VU1 unit** ON**

 Multi Threaded GS Mode  ** ON**
 Dual Core Mode **ON**

Frame limiting I've tired Normal, Frame Skip and VU Skip, no improvements.


I've noticed that the BIOS loading screen with the cubes is about 15-20.  After I get to the menus everything is fine.

Although trying to test the BIOS this morning leads me into another problem, I hit RUN CD or Execute (with no CD in drive) to try to bring BIOS up, and I get a black screen running at 250 FPS with nothing happening.  Nothing's changed since yesterday, so I have no idea.

Sorry I'm late with this, I don't check these boards much anymore.

I'll bet a dollar (or equivalent currency) you've got GL_SYNC_TO_VBLANK enabled.  The emulator does NOT place nicely with sync to vblank.

---

### Post by brodiepearce on 2007-06-18
I can't get this to compile from source, and if I extract it from a tarball instead, it won't correctly load the plugins:

<snip>

*edit*
I tried running it as sudo from the terminal, since I untarred it as sudo, that's probably would caused it to fail.  Seems to work fine now, haven't tested it with any roms yet though.

---

### Post by Sikarian on 2007-06-18
> **buttons said:**
> Sorry I'm late with this, I don't check these boards much anymore.

I'll bet a dollar (or equivalent currency) you've got GL_SYNC_TO_VBLANK enabled.  The emulator does NOT place nicely with sync to vblank.


I checked my nvidia-settings and my xorg.conf and couldn't see anything GL_SYNC_TO_VBLANK related.

Where might I find this option hiding?

---

### Post by Repent on 2007-06-18
OK I receive this error how can I correct it?

And at the risk of sounding really dumb how do you install the Nvidia Cg-Toolkit?

zerogs.h:36:19: error: Cg/cg.h: No such file or directory
zerogs.h:37:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:119: error: &#8216;CGprogram&#8217; does not name a type
zerogs.h:127: error: &#8216;CGprogram&#8217; does not name a type
zerogs.h:128: error: &#8216;CGparameter&#8217; does not name a type
zerogs.h:129: error: &#8216;CGparameter&#8217; does not name a type
zerogs.h:130: error: &#8216;CGparameter&#8217; does not name a type
zerogs.h: In constructor &#8216;FRAGMENTSHADER::FRAGMENTSHADER()&#8217;:
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;prog&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sMemory&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sFinal&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sBitwiseANDX&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sBitwiseANDY&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sInterlace&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sCLUT&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sOneColor&#8217;
zerogs.h:123: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;sBitBltZ&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexAlpha2&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexOffset&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexDims&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexBlock&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fClampExts&#8217;
zerogs.h:124: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexWrapMode&#8217;
zerogs.h:125: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fRealTexDims&#8217;
zerogs.h:125: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTestBlack&#8217;
zerogs.h:125: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fPageOffset&#8217;
zerogs.h:125: error: class &#8216;FRAGMENTSHADER&#8217; does not have any field named &#8216;fTexAlpha&#8217;
zerogs.h: At global scope:
zerogs.h:140: error: &#8216;CGprogram&#8217; does not name a type
zerogs.h:141: error: &#8216;CGparameter&#8217; does not name a type
zerogs.h: In constructor &#8216;VERTEXSHADER::VERTEXSHADER()&#8217;:
zerogs.h:139: error: class &#8216;VERTEXSHADER&#8217; does not have any field named &#8216;prog&#8217;
zerogs.h:139: error: class &#8216;VERTEXSHADER&#8217; does not have any field named &#8216;sBitBltPos&#8217;
zerogs.h:139: error: class &#8216;VERTEXSHADER&#8217; does not have any field named &#8216;sBitBltTex&#8217;
zerogs.h: At global scope:
zerogs.h:171: error: &#8216;CGparameter&#8217; does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: &#8216;CGcontext&#8217; does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: &#8216;CGprogram&#8217; does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/joe203/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
joe203@joe203-desktop:~/pcsx2$ 

Thanks
Repent

---

### Post by Jimbob17 on 2007-06-19
> **Repent said:**
> OK I receive this error how can I correct it?

And at the risk of sounding really dumb how do you install the Nvidia Cg-Toolkit?

* Snipped* 


All I did was to download CG from Nvidia as an RPM and use alien to change it into a .DEB file, then install.

---

### Post by Repent on 2007-06-19
How exactly do you use this? I put the game in and nothing happens.

---

### Post by Repent on 2007-06-21
Any one out there?

---

### Post by Mizarus on 2007-06-21
iam curious about performance , what are your specs(of somone who managed to get it working) and how well it worked, last time i tryed pscx2 (on windows) i coudnt get a playable fps rate i might give it a try under ubuntu.

---

### Post by Repent on 2007-06-23
Wow does anyone look at this forum anymore?

---

### Post by buttons on 2007-06-23
> **Mizarus said:**
> iam curious about performance , what are your specs(of somone who managed to get it working) and how well it worked, last time i tryed pscx2 (on windows) i coudnt get a playable fps rate i might give it a try under ubuntu.

Playable framerate requires an overclocked core 2 duo.  Some graphics-intensive games like resident evil are going to also require a decent video card (read: 7600gt or better).  People will sugarcoat this but that's the reality.

---

### Post by buttons on 2007-06-23
> **Sikarian said:**
> I checked my nvidia-settings and my xorg.conf and couldn't see anything GL_SYNC_TO_VBLANK related.

Where might I find this option hiding?

Nvidia-settings, under opengl settings.  Uncheck sync to vblank.  If you're running a desktop compositer, kill it before running the emulator.

---

### Post by Mizarus on 2007-06-23
> **buttons said:**
> Playable framerate requires an overclocked core 2 duo.  Some graphics-intensive games like resident evil are going to also require a decent (read: 7600gt or better).  People will sugarcoat this but that's the reality.
hm intresting, i figured id need a duo core so my 3700 single core wont be enough, but i tought i would need at least a 7800 to run this, if a 7600gt can do it my 6800gs most likely can do the job as welll when i upgrade my core il give it a try ty for the input.

---

### Post by buttons on 2007-06-23
> **Repent said:**
> How exactly do you use this? I put the game in and nothing happens.

You also have to run the program.

(Give details.  Your question tells us nothing.)

---

### Post by buttons on 2007-06-23
> **Mizarus said:**
> hm intresting, i figured id need a duo core so my 3700 single core wont be enough, but i tought i would need at least a 7800 to run this, if a 7600gt can do it my 6800gs most likely can do the job as welll when i upgrade my core il give it a try ty for the input.

Bitterness: I have a 7800gt and can barely run most games on my 2.6 Ghz dual core AMD x2.

If you're terribly curious, developer zerofrog posted a small novel on the [PCSX2 blog]("http://www.pcsx2.net/blog.php") entitled "PCSX2 Optimization," which details some of the problems with offloading work to the graphics card and simultaneously making emulation playable.  You'll have to scroll down a bit to find it, as the blog posts cannot be linked directly.

Anyway, yes, your 6800GS will most likely be fine for most games.

It should be noted that zerofrog is planning a large update to the opengl rendering engine for the next version, and all of this may change.

---

### Post by Repent on 2007-06-23
OK so how do you run the program,  please excuse me I'm not too bright.

---

### Post by buttons on 2007-06-24
If you have followed the instructions in the first post in order to compile it from SVN, the program can be run by going to the directory you installed it into, choosing the bin folder, and then running pcsx2.

You will want to change some of the settings under Config, such as enabling all of the recompilers in the ZeroGS plugin, and multicore support if you have it.  Also, you should select a dvdrom plugin so that you can run your games from the discs themselves, which your first post implies you have.

You will also need to have a PS2 bios in your pcsx2/bin/bios folder.  This can be dumped from your PS2 using instructions found elsewhere.  You can also er....find them.

After that, clicking Run CD from the file menu in pcsx2 will run your game.

---

### Post by Depressed Man on 2007-07-02
Do you still use the CG Nvidia toolkit even if your using an ATI card?

---

### Post by HectorSmarties on 2007-07-02
This emulator rocks! Too bad it needs a beefed-up PC to run a game properly. :/

---

### Post by Sockerdrickan on 2007-07-02
Can I get 30FPS in RE4? watch my sig
64bit and dual core will be used

---

### Post by Depressed Man on 2007-07-03
Always seem to come to a halt here.. I read that installing the GC Nvidia kit may help, but I'm using an ATI card so should I still install it? 

```
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
In file included from GSmain.cpp:39:
zerogs.h:36:19: error: Cg/cg.h: No such file or directory
zerogs.h:37:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:119: error: ‘CGprogram’ does not name a type
zerogs.h:127: error: ‘CGprogram’ does not name a type
zerogs.h:128: error: ‘CGparameter’ does not name a type
zerogs.h:129: error: ‘CGparameter’ does not name a type
zerogs.h:130: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:123: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:124: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:125: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:140: error: ‘CGprogram’ does not name a type
zerogs.h:141: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:139: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:171: error: ‘CGparameter’ does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/vforviktor/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins

```

---

### Post by brodiepearce on 2007-07-04
> **Depressed Man said:**
> Always seem to come to a halt here.. I read that installing the GC Nvidia kit may help, but I'm using an ATI card so should I still install it? 

```
----------------------
<snip>

```

Yes, you should still install the Nvideo CG tools.  I have an ATI card as well and it worked for me.  Now for something more trivial, how do I actually run PCSX2 after compiling from SVN source as in the original post?

*edit*
So I found the pcsx2/bin directory, so that's settled.

When I try to load my GT4 iso I get this error:

*edit*

OK so that was due to no BIOS being present, that is taken care of.  Now when I load my GT4 iso, it goes to the screen that you usually get on a PS2 when there's no disk inserted.  (Where you choose from  memory card or browser etc.).  I get this problem with both the V12 PAL BIOS and the V12 USA BIOS'.

---

### Post by Depressed Man on 2007-07-05
Thanks, the graphics plugin compiled. But it seems now I got another problem (oh vey..)

```
------------------------
Building SPU2 plugins...
------------------------
------------------
Building PeopsSPU2
------------------
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  spu.c
In file included from spu.c:235:
adsr.c: In function ‘MixADSR’:
adsr.c:85: warning: pointer targets in assignment differ in signedness
adsr.c:86: warning: pointer targets in assignment differ in signedness
adsr.c:87: warning: pointer targets in assignment differ in signedness
adsr.c:115: warning: pointer targets in assignment differ in signedness
adsr.c:116: warning: pointer targets in assignment differ in signedness
adsr.c:117: warning: pointer targets in assignment differ in signedness
spu.c: In function ‘MainSPU2Proc’:
spu.c:585: warning: left-hand operand of comma expression has no effect
spu.c:585: warning: left-hand operand of comma expression has no effect
spu.c:595: warning: left-hand operand of comma expression has no effect
spu.c:595: warning: left-hand operand of comma expression has no effect
spu.c: In function ‘SPU2init’:
spu.c:987: warning: pointer targets in assignment differ in signedness
spu.c: In function ‘SetupStreams’:
spu.c:1095: warning: pointer targets in assignment differ in signedness
spu.c:1096: warning: pointer targets in assignment differ in signedness
spu.c:1097: warning: pointer targets in assignment differ in signedness
spu.c: In function ‘SPU2open’:
spu.c:1134: warning: pointer targets in assignment differ in signedness
spu.c:1136: warning: pointer targets in assignment differ in signedness
spu.c:1137: warning: pointer targets in assignment differ in signedness
spu.c:1126: warning: unused variable ‘dsp’
spu.c: At top level:
spu.c:135: warning: ‘libraryInfo’ defined but not used
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  dma.c
dma.c: In function ‘SPU2writeDMA4Mem’:
dma.c:219: warning: pointer targets in assignment differ in signedness
dma.c:339:2: warning: no newline at end of file
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  freeze.c
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  registers.c
registers.c:71: warning: type defaults to ‘int’ in declaration of ‘chanmap’
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  alsa.c
alsa.c:40:28: error: alsa/asoundlib.h: No such file or directory
alsa.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alsa.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buffer_size’
alsa.c: In function ‘SetupSound’:
alsa.c:68: error: ‘snd_pcm_hw_params_t’ undeclared (first use in this function)
alsa.c:68: error: (Each undeclared identifier is reported only once
alsa.c:68: error: for each function it appears in.)
alsa.c:68: error: ‘hwparams’ undeclared (first use in this function)
alsa.c:69: error: ‘snd_pcm_sw_params_t’ undeclared (first use in this function)
alsa.c:69: error: ‘swparams’ undeclared (first use in this function)
alsa.c:70: error: ‘snd_pcm_status_t’ undeclared (first use in this function)
alsa.c:70: error: ‘status’ undeclared (first use in this function)
alsa.c:82: error: ‘SND_PCM_FORMAT_S16_LE’ undeclared (first use in this function)
alsa.c:86: warning: implicit declaration of function ‘snd_pcm_open’
alsa.c:86: error: ‘handle’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_STREAM_PLAYBACK’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_NONBLOCK’ undeclared (first use in this function)
alsa.c:89: warning: implicit declaration of function ‘snd_strerror’
alsa.c:89: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:93: warning: implicit declaration of function ‘snd_pcm_nonblock’
alsa.c:95: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:99: warning: implicit declaration of function ‘snd_pcm_hw_params_alloca’
alsa.c:100: warning: implicit declaration of function ‘snd_pcm_sw_params_alloca’
alsa.c:101: warning: implicit declaration of function ‘snd_pcm_hw_params_any’
alsa.c:103: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:107: warning: implicit declaration of function ‘snd_pcm_hw_params_set_access’
alsa.c:107: error: ‘SND_PCM_ACCESS_RW_INTERLEAVED’ undeclared (first use in this function)
alsa.c:109: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:113: warning: implicit declaration of function ‘snd_pcm_hw_params_set_format’
alsa.c:115: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:119: warning: implicit declaration of function ‘snd_pcm_hw_params_set_channels’
alsa.c:121: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:125: warning: implicit declaration of function ‘snd_pcm_hw_params_set_rate_near’
alsa.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:131: warning: implicit declaration of function ‘snd_pcm_hw_params_set_buffer_time_near’
alsa.c:133: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:137: warning: implicit declaration of function ‘snd_pcm_hw_params_set_period_time_near’
alsa.c:139: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:143: warning: implicit declaration of function ‘snd_pcm_hw_params’
alsa.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:149: warning: implicit declaration of function ‘snd_pcm_status_alloca’
alsa.c:150: warning: implicit declaration of function ‘snd_pcm_status’
alsa.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:156: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c:156: warning: implicit declaration of function ‘snd_pcm_status_get_avail’
alsa.c: In function ‘RemoveSound’:
alsa.c:165: error: ‘handle’ undeclared (first use in this function)
alsa.c:167: warning: implicit declaration of function ‘snd_pcm_drop’
alsa.c:168: warning: implicit declaration of function ‘snd_pcm_close’
alsa.c: In function ‘SoundGetBytesBuffered’:
alsa.c:181: error: ‘handle’ undeclared (first use in this function)
alsa.c:183: warning: implicit declaration of function ‘snd_pcm_avail_update’
alsa.c:185: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c: In function ‘SoundFeedVoiceData’:
alsa.c:198: error: ‘handle’ undeclared (first use in this function)
alsa.c:200: warning: implicit declaration of function ‘snd_pcm_state’
alsa.c:200: error: ‘SND_PCM_STATE_XRUN’ undeclared (first use in this function)
alsa.c:201: warning: implicit declaration of function ‘snd_pcm_prepare’
alsa.c:202: warning: implicit declaration of function ‘snd_pcm_writei’
make: *** [alsa.o] Error 1
Error with building plugins

```

---

### Post by Sockerdrickan on 2007-07-05
Might wanna get some alsa dev files

---

### Post by jimminy_kriket on 2007-07-08
Sorry for the noob question, but where is the actuall program? i found a pcsx2 folder in my home directory, went into the bin folder, but what do I run from there? i looked in all the folders but didnt find the actual program >_<

What file do I run? Sorry im pretty new to this.

---

### Post by brodiepearce on 2007-07-09
> **jimminy_kriket said:**
> Sorry for the noob question, but where is the actuall program? i found a pcsx2 folder in my home directory, went into the bin folder, but what do I run from there? i looked in all the folders but didnt find the actual program >_<

What file do I run? Sorry im pretty new to this.

You run the pcsx2 file in the bin directory, E.g. "./pcsx2" from terminal or something similar to do it in a launcher.  It should already be executable, but if it's not do "chmod +x pcsx2" on it.

[QUOTE=Depressed Man]
<snip>
[/QUOTE]

Do:

```

sudo apt-get install libasound2-dev

```

---

### Post by jimminy_kriket on 2007-07-09
[IMG]http://i12.tinypic.com/5xruquq.png[/IMG]

That is my pcsx2/bin folder, I probably have to recompile dont I ? =(

---

### Post by brodiepearce on 2007-07-09
> **jimminy_kriket said:**
> 
That is my pcsx2/bin folder, I probably have to recompile dont I ? =(

Hmm, not sure why you would end up with a folder hierarchy like that, but this is what my ~/pcsx2/bin looks like:

---

### Post by cleverselfreferentialname on 2007-07-11
> **Tux0r said:**
> It's not shitty because you don't know how to compile it.

Oh, I compiled it. _Surprisingly_, it got that far without segfaulting.

---

### Post by sentofuno on 2007-07-12
> **buttons said:**
> You're missing the [Cg Toolkit]("http://developer.nvidia.com/object/cg_toolkit.html") from nVidia.

Easiest way to install it is to grab [this RPM]("http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007.i386.rpm") (32-bit) and then do the following in whatever directory you downloaded it into:
```
sudo apt-get install alien
alien Cg-1.5_Feb2007.i386.rpm
sudo dpkg -i Cg-1.5_Feb2007.i386.deb
```

Then start your sh build.sh all again.

sorry to have to ask, but i'm a noob and have gotten as far as i have by copy/pasting code fields (thanks a lot for the instructions so far)

i tried the above and it aborts after i confirm it can continue. i assume its because i have x64 feisty fawn and not i386. i tried editing the above to:

sudo apt-get install alien
alien Cg-1.5_Feb2007.x86_64.rpm
sudo dpkg -i Cg-1.5_Feb2007.x86_64.deb


unfortunately no cigar for blind guessing. can anyone get me rolling again? or at least tell me where i'm going wrong? i'm not averse to trying or guessing but i could use some help

cheers

---

### Post by jimminy_kriket on 2007-07-12
[http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86_64.tar.gz](http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86_64.tar.gz)

That is the one you will need. Or you could force the i386 one. Unfortunatly I am still learning and dont know the commands to do things like this.

---

### Post by sentofuno on 2007-07-12
i downloaded that in the meantime and tried a couple of guesses to .deb it with alien but couldn't get it working, i don't know the command syntax. cheers for repying tho.

---

### Post by Sockerdrickan on 2007-07-12
> **cleverselfreferentialname said:**
> Oh, I compiled it. _Surprisingly_, it got that far without segfaulting.
Okay all good then

---

### Post by melchiorre on 2007-08-16
> **BorjaRRR said:**
> When i run pcsx2 happens this :


ZeroGS window is black but fps continue counting
Any solution?
Sorry for my bad english ;)

I've the same problem, ZeroGS window is black and then crash (the sound is good)

P.S. This is the bash output:

[QUOTEZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.2
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: ******
ZeroGS: GS WARNING: Floating point render targets not supported, switching to 32bit
ZeroGS: *********
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32768
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36864
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40960
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45056
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32769
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36865
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40961
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45057
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32770
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36866
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40962
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45058
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 32771
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 36867
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 40963
ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45059
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
Segmentation fault (core dumped)
][/QUOTE]

---

### Post by buttons on 2007-08-16
Hmm.  Try reinstalling Cg-toolkit?

---

### Post by jacob01 on 2007-08-16
what is it is it a game

---

### Post by Avatarius on 2007-08-17
Same Problem here:

> ZeroGS: Cg error: CG ERROR : The program could not load.
ZeroGS: failed to load program 45059
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
Segmentation fault (core dumped)


I have re-installed cg-toolkit but the error still occurs.

With the pre-compiled linux binaries it's the same problem.

Any suggestions ?

---

### Post by buttons on 2007-08-17
> **Avatarius said:**
> Same Problem here:



I have re-installed cg-toolkit but the error still occurs.

With the pre-compiled linux binaries it's the same problem.

Any suggestions ?

I haven't seen that one before, unfortunately.  I suggest filing a bug report on their official forums.  There are instructions [here]("http://ubuntuforums.org/showthread.php?t=399165&p=2630121").

---

### Post by Surkow on 2007-08-31
I compiled version 0.9.3 from the main page and I'm able to have around 60-80fps ingame. Even though I now hear robotic sounds, the sound plugin configuration still fails to load. I also have a problem with not being able to use the controllers/gamepads I attached to my pc. The ZeroPAD plugin does not react to the input (I presume the other is for windows since the GUI is distorted and not reacting to input from the controller either). I currently use a Piranha gamepad because my Xbox360 controller won't be recognized at all by Ubuntu (It should according to various guides - but it does not create a device node in /dev/input).

---

### Post by acoustibop on 2007-08-31
> **jacob01 said:**
> what is it is it a game

It's a Playstation 2 emulator, jacob01.  You can play Playstation 2 games in it, although you'll need a fairly high end machine.

---

### Post by CryptiniteDemon on 2007-09-02
Okay, so I compiled it and everything, but stupid question here, how do I run it?

---

### Post by Sparckus on 2007-09-07
I take it this doesn't work with ATI cards if you need the nvidia CG-Toolkit ?

---

### Post by Egnoc on 2007-09-07
I used the first page to install PCSX2 but I was in root when I did it. Now I'm getting permission problems. 

Is there any way to reverse the process. 

(BTW, I am a Linux n00b but I think it's about time to learn)

---

### Post by Surkow on 2007-09-11
> **Egnoc said:**
> I used the first page to install PCSX2 but I was in root when I did it. Now I'm getting permission problems. 

Is there any way to reverse the process. 

(BTW, I am a Linux n00b but I think it's about time to learn)
Go back to the root user account and change the permissions by hand to your other user.

---

### Post by Lacrimstein on 2007-09-13
I tried to compile, but i got the following error(s):

> Building SPU2 plugins...
------------------------
------------------
Building PeopsSPU2
------------------
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  alsa.c
alsa.c:40:28: error: alsa/asoundlib.h: No such file or directory
alsa.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alsa.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buffer_size’
alsa.c: In function ‘SetupSound’:
alsa.c:68: error: ‘snd_pcm_hw_params_t’ undeclared (first use in this function)
alsa.c:68: error: (Each undeclared identifier is reported only once
alsa.c:68: error: for each function it appears in.)
alsa.c:68: error: ‘hwparams’ undeclared (first use in this function)
alsa.c:69: error: ‘snd_pcm_sw_params_t’ undeclared (first use in this function)
alsa.c:69: error: ‘swparams’ undeclared (first use in this function)
alsa.c:70: error: ‘snd_pcm_status_t’ undeclared (first use in this function)
alsa.c:70: error: ‘status’ undeclared (first use in this function)
alsa.c:82: error: ‘SND_PCM_FORMAT_S16_LE’ undeclared (first use in this function)
alsa.c:86: warning: implicit declaration of function ‘snd_pcm_open’
alsa.c:86: error: ‘handle’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_STREAM_PLAYBACK’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_NONBLOCK’ undeclared (first use in this function)
alsa.c:89: warning: implicit declaration of function ‘snd_strerror’
alsa.c:89: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:93: warning: implicit declaration of function ‘snd_pcm_nonblock’
alsa.c:95: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:99: warning: implicit declaration of function ‘snd_pcm_hw_params_alloca’
alsa.c:100: warning: implicit declaration of function ‘snd_pcm_sw_params_alloca’
alsa.c:101: warning: implicit declaration of function ‘snd_pcm_hw_params_any’
alsa.c:103: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:107: warning: implicit declaration of function ‘snd_pcm_hw_params_set_access’
alsa.c:107: error: ‘SND_PCM_ACCESS_RW_INTERLEAVED’ undeclared (first use in this function)
alsa.c:109: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:113: warning: implicit declaration of function ‘snd_pcm_hw_params_set_format’
alsa.c:115: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:119: warning: implicit declaration of function ‘snd_pcm_hw_params_set_channels’
alsa.c:121: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:125: warning: implicit declaration of function ‘snd_pcm_hw_params_set_rate_near’
alsa.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:131: warning: implicit declaration of function ‘snd_pcm_hw_params_set_buffer_time_near’
alsa.c:133: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:137: warning: implicit declaration of function ‘snd_pcm_hw_params_set_period_time_near’
alsa.c:139: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:143: warning: implicit declaration of function ‘snd_pcm_hw_params’
alsa.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:149: warning: implicit declaration of function ‘snd_pcm_status_alloca’
alsa.c:150: warning: implicit declaration of function ‘snd_pcm_status’
alsa.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:156: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c:156: warning: implicit declaration of function ‘snd_pcm_status_get_avail’
alsa.c: In function ‘RemoveSound’:
alsa.c:165: error: ‘handle’ undeclared (first use in this function)
alsa.c:167: warning: implicit declaration of function ‘snd_pcm_drop’
alsa.c:168: warning: implicit declaration of function ‘snd_pcm_close’
alsa.c: In function ‘SoundGetBytesBuffered’:
alsa.c:181: error: ‘handle’ undeclared (first use in this function)
alsa.c:183: warning: implicit declaration of function ‘snd_pcm_avail_update’
alsa.c:185: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c: In function ‘SoundFeedVoiceData’:
alsa.c:198: error: ‘handle’ undeclared (first use in this function)
alsa.c:200: warning: implicit declaration of function ‘snd_pcm_state’
alsa.c:200: error: ‘SND_PCM_STATE_XRUN’ undeclared (first use in this function)
alsa.c:201: warning: implicit declaration of function ‘snd_pcm_prepare’
alsa.c:202: warning: implicit declaration of function ‘snd_pcm_writei’


---

### Post by markp1989 on 2007-09-14
where can i get the ps2 bios,i own 2 ps2s so i am legally allowed to get it right?

---

### Post by Sockerdrickan on 2007-09-14
no

---

### Post by Sparckus on 2007-09-14
> **markp1989 said:**
> where can i get the ps2 bios,i own 2 ps2s so i am legally allowed to get it right?

[http://www.pcsx2.net/downloads.php?p=tool]("http://www.pcsx2.net/downloads.php?p=tool")

Relevant thread:

[http://forums.ngemu.com/pcsx2-official-forum/91175-bios-dumper-v2-0-a.html]("http://forums.ngemu.com/pcsx2-official-forum/91175-bios-dumper-v2-0-a.html")

:Edit:

This is the only legal way you can obtain a PS2 BIOS i.e. your own

---

### Post by markp1989 on 2007-09-14
> **Sparckus said:**
> [http://www.pcsx2.net/downloads.php?p=tool]("http://www.pcsx2.net/downloads.php?p=tool")

Relevant thread:

[http://forums.ngemu.com/pcsx2-official-forum/91175-bios-dumper-v2-0-a.html]("http://forums.ngemu.com/pcsx2-official-forum/91175-bios-dumper-v2-0-a.html")

:Edit:

This is the only legal way you can obtain a PS2 BIOS i.e. your own

so im meant to dump the bios on my ps2 to a file somehow, the top link you sent me wasto an iso, but my playstation is not chipped, so how do i boot copy disks? 

my play station two runs the play station 2 independent exploit, if thats any help?

---

### Post by Sparckus on 2007-09-15
> **markp1989 said:**
> so im meant to dump the bios on my ps2 to a file somehow, the top link you sent me wasto an iso, but my playstation is not chipped, so how do i boot copy disks? 

my play station two runs the play station 2 independent exploit, if thats any help?

The guide actually recommends that you PS2 isnt chipped, you need either a flash drive to dump the file.  I'll burn it and test it later, i havent used this particular one yet myself.

---

### Post by pyrokenx on 2007-09-17
Following as much information as I could find thus far, I am still unable to compile this either from tarball release or from SVN, the binary doesnt work either.

I am using an amd64 setup, I have tried on both feisty and gutsy, both svn and stable release, and am still unable to compile.  When using the available binaries I get an error about not finding libCG at the beginning and that I Couldnt load the GS plugin., I have libCG installed, plus its sitting right with the program itself...


Would anyone please take the time to make a Deb file? :)

EDIT: as luck would have it, I managed to fix my problems on my own immediately after making this post ;p

What I did: I install cg toolkit from synaptic (yeah I know I am retarded), then I just downloaded the binary tarball from pcsx2.net

However, my problem in compiling still exists, but it no longer affects me.

---

### Post by process91 on 2007-10-07
Buttons I need you!

I have a problem playing any and all games with PCSX2, even the bios loader crashes after just a couple of seconds. I started a thread [here]("http://ubuntuforums.org/showthread.php?t=569191&highlight=pcsx2"), and then I started digging deeper. It seems that the ZeroGS plugin which comes with PCSX2 doesn't work with cards that don't support pixel shading 2. My card supports 3 and 4, but not 2. Therefore I needed to switch to a different plugin. After  downloading GSSoft 0.61 and putting the .so file into my plugins directory it would not show up in the list.

I then proceeded to download the source for the plugin (it was actually still in my SVN download directory) and compile it, but when I run build.sh in the GS folder it doesn't build the GSSoft plugin, only the ZeroGS plugin. I tried to go into the GSSoft folder and run a make/make install but the make came up with errors.

Any suggestions would be great!

---

### Post by antmangaka on 2007-10-12
hello i have cd toolkit but zeroOpengl fails to compile :(
```
minyie@minyie-desktop:~/Installers/pcsx2$ sudo sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-memcpy_amd.o -MD -MP -MF ".deps/libZeroGSogl_a-memcpy_amd.Tpo" -c -o libZeroGSogl_a-memcpy_amd.o `test -f 'memcpy_amd.cpp' || echo './'`memcpy_amd.cpp; \
        then mv -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo" ".deps/libZeroGSogl_a-memcpy_amd.Po"; else rm -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Regs.o -MD -MP -MF ".deps/libZeroGSogl_a-Regs.Tpo" -c -o libZeroGSogl_a-Regs.o `test -f 'Regs.cpp' || echo './'`Regs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Regs.Tpo" ".deps/libZeroGSogl_a-Regs.Po"; else rm -f ".deps/libZeroGSogl_a-Regs.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-x86.o -MD -MP -MF ".deps/libZeroGSogl_a-x86.Tpo" -c -o libZeroGSogl_a-x86.o `test -f 'x86.cpp' || echo './'`x86.cpp; \
        then mv -f ".deps/libZeroGSogl_a-x86.Tpo" ".deps/libZeroGSogl_a-x86.Po"; else rm -f ".deps/libZeroGSogl_a-x86.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zpipe.o -MD -MP -MF ".deps/libZeroGSogl_a-zpipe.Tpo" -c -o libZeroGSogl_a-zpipe.o `test -f 'zpipe.cpp' || echo './'`zpipe.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zpipe.Tpo" ".deps/libZeroGSogl_a-zpipe.Po"; else rm -f ".deps/libZeroGSogl_a-zpipe.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Mem.o -MD -MP -MF ".deps/libZeroGSogl_a-Mem.Tpo" -c -o libZeroGSogl_a-Mem.o `test -f 'Mem.cpp' || echo './'`Mem.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Mem.Tpo" ".deps/libZeroGSogl_a-Mem.Po"; else rm -f ".deps/libZeroGSogl_a-Mem.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-rasterfont.o -MD -MP -MF ".deps/libZeroGSogl_a-rasterfont.Tpo" -c -o libZeroGSogl_a-rasterfont.o `test -f 'rasterfont.cpp' || echo './'`rasterfont.cpp; \
        then mv -f ".deps/libZeroGSogl_a-rasterfont.Tpo" ".deps/libZeroGSogl_a-rasterfont.Po"; else rm -f ".deps/libZeroGSogl_a-rasterfont.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-targets.o -MD -MP -MF ".deps/libZeroGSogl_a-targets.Tpo" -c -o libZeroGSogl_a-targets.o `test -f 'targets.cpp' || echo './'`targets.cpp; \
        then mv -f ".deps/libZeroGSogl_a-targets.Tpo" ".deps/libZeroGSogl_a-targets.Po"; else rm -f ".deps/libZeroGSogl_a-targets.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zerogs.o -MD -MP -MF ".deps/libZeroGSogl_a-zerogs.Tpo" -c -o libZeroGSogl_a-zerogs.o `test -f 'zerogs.cpp' || echo './'`zerogs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zerogs.Tpo" ".deps/libZeroGSogl_a-zerogs.Po"; else rm -f ".deps/libZeroGSogl_a-zerogs.Tpo"; exit 1; fi
zerogs.cpp:321: warning: non-local variable ‘<anonymous union> g_vars’ uses anonymous type
zerogs.cpp: In function ‘void ZeroGS::HandleGLError()’:
zerogs.cpp:892: error: ‘GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT’ was not declared in this scope
make[1]: *** [libZeroGSogl_a-zerogs.o] Error 1
make[1]: Leaving directory `/home/minyie/Installers/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
minyie@minyie-desktop:~/Installers/pcsx2$ make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
> make: *** [install-recursive] Error 1make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
> make: *** [install-recursive] Error 1make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: make[1]:: command not found
minyie@minyie-desktop:~/Installers/pcsx2$ make: *** [install-recursive] Error 1make[1]: Leaving directory `/home/jon/pcsx2/plugins/gs/zerogs/opengl'
> make: *** [install-recursive] Error 1

```
hat can i do?

---

### Post by Einar89 on 2007-10-16
I seem to have a very weird problem(beyond the fact that I can`t register on the ngemu forums): I`m trying to play FFX, and all the geometry(except for the characters) is well..misplaced...there are polygons everywhere. Any ideas?

---

### Post by Bwoolgar on 2007-10-16
I'm having the same problem as antman. Anyone know of a fix?

EDIT: The only info that I've found is that it has to do with mesa and a "renderbuffer that is attached more than once." :confused:

---

### Post by nonite on 2007-10-18
> **Bwoolgar said:**
> I'm having the same problem as antman. Anyone know of a fix?

EDIT: The only info that I've found is that it has to do with mesa and a "renderbuffer that is attached more than once." :confused:

I'm having the same problem. I seem to have unfortunately lost the link, but i have read in some forum that its a bug in the new version of mesa-common-dev (version 7.0). One possible solution is to downgrade to the old version (6.5 I think).However I'm not sure about dependencies and I was unable to get it from repositories (guess its not there anymore). I didn't have time to look for more solutions so far, maybe it would be best to wait for a fix?

---

### Post by dhqk on 2007-10-20
Hi im no pro but this is what i tried, i did a internet search for the Constant and found that it was equal to this 0x8CD8 so i replaced the GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT with that and it compiled, good luck =)

---

### Post by Hobo2021 on 2007-10-21
> **dhqk said:**
> Hi im no pro but this is what i tried, i did a internet search for the Constant and found that it was equal to this 0x8CD8 so i replaced the GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT with that and it compiled, good luck =)

Where exactly did you replace it?

---

### Post by Kelvari on 2007-10-22
Found the solution to theGL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT  problem at [http://forums.ngemu.com/pcsx2-official-forum/94388-compil-error-pcsx2-0-9-3-svn.html](http://forums.ngemu.com/pcsx2-official-forum/94388-compil-error-pcsx2-0-9-3-svn.html)

Credit to EleQusion for posting the solution.
> To fix the GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT error, goto /pcsx2/plugins/gs/zerogs/opengl/zerogs.cpp and remove the case;

case GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT :
ERROR_LOG("Error! has an image/buffer attached in multiple locations!\n");
break;

The reason why this happens is because the feature was removed in version 117 of the GL_EXT_framebuffer_object spec]

Just comment out lines 892 - 894

---

### Post by Wodzu on 2007-11-04
> **Lacrimstein said:**
> I tried to compile, but i got the following error(s):
Quote:
Building SPU2 plugins...
------------------------
------------------
Building PeopsSPU2
------------------
gcc -fPIC -c -Wall -O3 -ffast-math -fomit-frame-pointer -DUSEALSA alsa.c
alsa.c:40:28: error: alsa/asoundlib.h: No such file or directory
alsa.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alsa.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buffer_size’
alsa.c: In function ‘SetupSound’:
alsa.c:68: error: ‘snd_pcm_hw_params_t’ undeclared (first use in this function)
alsa.c:68: error: (Each undeclared identifier is reported only once
alsa.c:68: error: for each function it appears in.)
alsa.c:68: error: ‘hwparams’ undeclared (first use in this function)
alsa.c:69: error: ‘snd_pcm_sw_params_t’ undeclared (first use in this function)
alsa.c:69: error: ‘swparams’ undeclared (first use in this function)
alsa.c:70: error: ‘snd_pcm_status_t’ undeclared (first use in this function)
alsa.c:70: error: ‘status’ undeclared (first use in this function)
alsa.c:82: error: ‘SND_PCM_FORMAT_S16_LE’ undeclared (first use in this function)
alsa.c:86: warning: implicit declaration of function ‘snd_pcm_open’
alsa.c:86: error: ‘handle’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_STREAM_PLAYBACK’ undeclared (first use in this function)
alsa.c:87: error: ‘SND_PCM_NONBLOCK’ undeclared (first use in this function)
alsa.c:89: warning: implicit declaration of function ‘snd_strerror’
alsa.c:89: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:93: warning: implicit declaration of function ‘snd_pcm_nonblock’
alsa.c:95: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:99: warning: implicit declaration of function ‘snd_pcm_hw_params_alloca’
alsa.c:100: warning: implicit declaration of function ‘snd_pcm_sw_params_alloca’
alsa.c:101: warning: implicit declaration of function ‘snd_pcm_hw_params_any’
alsa.c:103: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:107: warning: implicit declaration of function ‘snd_pcm_hw_params_set_access’
alsa.c:107: error: ‘SND_PCM_ACCESS_RW_INTERLEAVED’ undeclared (first use in this function)
alsa.c:109: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:113: warning: implicit declaration of function ‘snd_pcm_hw_params_set_format’
alsa.c:115: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:119: warning: implicit declaration of function ‘snd_pcm_hw_params_set_channels’
alsa.c:121: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:125: warning: implicit declaration of function ‘snd_pcm_hw_params_set_rate_near’
alsa.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:131: warning: implicit declaration of function ‘snd_pcm_hw_params_set_buffer_time_near’
alsa.c:133: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:137: warning: implicit declaration of function ‘snd_pcm_hw_params_set_period_time_near’
alsa.c:139: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:143: warning: implicit declaration of function ‘snd_pcm_hw_params’
alsa.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:149: warning: implicit declaration of function ‘snd_pcm_status_alloca’
alsa.c:150: warning: implicit declaration of function ‘snd_pcm_status’
alsa.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
alsa.c:156: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c:156: warning: implicit declaration of function ‘snd_pcm_status_get_avail’
alsa.c: In function ‘RemoveSound’:
alsa.c:165: error: ‘handle’ undeclared (first use in this function)
alsa.c:167: warning: implicit declaration of function ‘snd_pcm_drop’
alsa.c:168: warning: implicit declaration of function ‘snd_pcm_close’
alsa.c: In function ‘SoundGetBytesBuffered’:
alsa.c:181: error: ‘handle’ undeclared (first use in this function)
alsa.c:183: warning: implicit declaration of function ‘snd_pcm_avail_update’
alsa.c:185: error: ‘buffer_size’ undeclared (first use in this function)
alsa.c: In function ‘SoundFeedVoiceData’:
alsa.c:198: error: ‘handle’ undeclared (first use in this function)
alsa.c:200: warning: implicit declaration of function ‘snd_pcm_state’
alsa.c:200: error: ‘SND_PCM_STATE_XRUN’ undeclared (first use in this function)
alsa.c:201: warning: implicit declaration of function ‘snd_pcm_prepare’
alsa.c:202: warning: implicit declaration of function ‘snd_pcm_writei’ 



sudo apt-get install libasound2-dev

---

### Post by mallegonian on 2007-11-04
Thank you, buttons, for the guide.

 I thought I had all of the required stuff installed but the graphics plugin wasn't working. For reference, I needed to install the libxxf86vm library.

---

### Post by cuihui on 2007-11-08
Hi, i pretty new with pcsx2 on ubuntu. I followed the instructions and i was able to compile everything. I haveing problem when executing the emulator. I can execute the program and as long as it is not running the cd it will going fine. If i open an iso cd, the program crash at the state where it shows up the "playstation"  word and bump "segmentation fault"

ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.2
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: ******
ZeroGS: GS WARNING: Floating point render targets not supported, switching to 32bit
ZeroGS: *********
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
Segmentation fault (core dumped)

System:
CPU: Centrino Duo 2.0GHz
Graphic: ATI Radeon X1400
Ram: 2GB
OS: Ubuntu
using fglrx

Anybody can help? Thanks.

cuihui

---

### Post by KevNice on 2007-11-11
ok, I tried to build this after installing the NVIDIA thing, and it gets pretty far but stops:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-memcpy_amd.o -MD -MP -MF ".deps/libZeroGSogl_a-memcpy_amd.Tpo" -c -o libZeroGSogl_a-memcpy_amd.o `test -f 'memcpy_amd.cpp' || echo './'`memcpy_amd.cpp; \
        then mv -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo" ".deps/libZeroGSogl_a-memcpy_amd.Po"; else rm -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Regs.o -MD -MP -MF ".deps/libZeroGSogl_a-Regs.Tpo" -c -o libZeroGSogl_a-Regs.o `test -f 'Regs.cpp' || echo './'`Regs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Regs.Tpo" ".deps/libZeroGSogl_a-Regs.Po"; else rm -f ".deps/libZeroGSogl_a-Regs.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-x86.o -MD -MP -MF ".deps/libZeroGSogl_a-x86.Tpo" -c -o libZeroGSogl_a-x86.o `test -f 'x86.cpp' || echo './'`x86.cpp; \
        then mv -f ".deps/libZeroGSogl_a-x86.Tpo" ".deps/libZeroGSogl_a-x86.Po"; else rm -f ".deps/libZeroGSogl_a-x86.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zpipe.o -MD -MP -MF ".deps/libZeroGSogl_a-zpipe.Tpo" -c -o libZeroGSogl_a-zpipe.o `test -f 'zpipe.cpp' || echo './'`zpipe.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zpipe.Tpo" ".deps/libZeroGSogl_a-zpipe.Po"; else rm -f ".deps/libZeroGSogl_a-zpipe.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Mem.o -MD -MP -MF ".deps/libZeroGSogl_a-Mem.Tpo" -c -o libZeroGSogl_a-Mem.o `test -f 'Mem.cpp' || echo './'`Mem.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Mem.Tpo" ".deps/libZeroGSogl_a-Mem.Po"; else rm -f ".deps/libZeroGSogl_a-Mem.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-rasterfont.o -MD -MP -MF ".deps/libZeroGSogl_a-rasterfont.Tpo" -c -o libZeroGSogl_a-rasterfont.o `test -f 'rasterfont.cpp' || echo './'`rasterfont.cpp; \
        then mv -f ".deps/libZeroGSogl_a-rasterfont.Tpo" ".deps/libZeroGSogl_a-rasterfont.Po"; else rm -f ".deps/libZeroGSogl_a-rasterfont.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-targets.o -MD -MP -MF ".deps/libZeroGSogl_a-targets.Tpo" -c -o libZeroGSogl_a-targets.o `test -f 'targets.cpp' || echo './'`targets.cpp; \
        then mv -f ".deps/libZeroGSogl_a-targets.Tpo" ".deps/libZeroGSogl_a-targets.Po"; else rm -f ".deps/libZeroGSogl_a-targets.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zerogs.o -MD -MP -MF ".deps/libZeroGSogl_a-zerogs.Tpo" -c -o libZeroGSogl_a-zerogs.o `test -f 'zerogs.cpp' || echo './'`zerogs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zerogs.Tpo" ".deps/libZeroGSogl_a-zerogs.Po"; else rm -f ".deps/libZeroGSogl_a-zerogs.Tpo"; exit 1; fi
zerogs.cpp:321: warning: non-local variable ‘<anonymous union> g_vars’ uses anonymous type
zerogs.cpp: In function ‘void ZeroGS::HandleGLError()’:
zerogs.cpp:892: error: ‘GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT’ was not declared in this scope
make[1]: *** [libZeroGSogl_a-zerogs.o] Error 1
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
kevin@kevin-laptop:~/pcsx2$ 


```

any ideas?

---

### Post by chronusdark on 2007-11-11
> **cuihui said:**
> Hi, i pretty new with pcsx2 on ubuntu. I followed the instructions and i was able to compile everything. I haveing problem when executing the emulator. I can execute the program and as long as it is not running the cd it will going fine. If i open an iso cd, the program crash at the state where it shows up the "playstation"  word and bump "segmentation fault"

ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.2
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: ******
ZeroGS: GS WARNING: Floating point render targets not supported, switching to 32bit
ZeroGS: *********
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
Segmentation fault (core dumped)

System:
CPU: Centrino Duo 2.0GHz
Graphic: ATI Radeon X1400
Ram: 2GB
OS: Ubuntu
using fglrx

Anybody can help? Thanks.

cuihui
 did you ever get it working i get the same error

---

### Post by Ferrat on 2007-11-11
Well I got everything fixed except the grafic driver

```
/pcsx2/bin/plugins/libZeroGSoglr.so.0.96.2: symbol cgIsParameterUsed, version VERSION not defined in file libCg.so with link time reference
```

This is what pops up, any ideas? it compiles fine and I get yes on everthing when it configures >_<

---

### Post by go_beep_yourself on 2007-11-11
> **buttons said:**
> C
It PROBABLY requires:
libglu1-mesa-dev


Why do you say probably requires?

---

### Post by ahmshaegar on 2007-11-12
Just to let everyone know...

PCSX2 0.9.4 was released today!  Well, yesterday where I am (it was released on Sunday, November 11, 2007.)

---

### Post by go_beep_yourself on 2007-11-12
What plugins are needed for pcsx2 to work? Are they included with the source code or do I have to download them separately? What can I do about this error?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=49975&d=1194870476[/IMG]

---

### Post by wildnr1 on 2007-11-18
> **Tux0r said:**
> It's not shitty because you don't know how to compile it.

Hello, 
after reading the whole guide I still can not get it to compile:
HELP needed, thanks;

Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
Making clean in .
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl' wordt binnengegaan
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl' wordt verlaten
Making install in Linux
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In bestand ingevoegd door Conf.cpp:25:
../GS.h:41:21: fout: GL/glew.h: Bestand of map bestaat niet
make[1]: *** [libZeroGSLinux_a-Conf.o] Fout 1
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
make: *** [install-recursive] Fout 1
Error with building plugins



hope's are high :)

---

### Post by L3oN on 2007-11-19
I've your same problem: [http://rafb.net/p/AafNkw38.html](http://rafb.net/p/AafNkw38.html)

---

### Post by go_beep_yourself on 2007-11-19
> **wildnr1 said:**
> Hello, 
after reading the whole guide I still can not get it to compile:
HELP needed, thanks;

Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
Making clean in .
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl' wordt binnengegaan
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl' wordt verlaten
Making install in Linux
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In bestand ingevoegd door Conf.cpp:25:
../GS.h:41:21: fout: GL/glew.h: Bestand of map bestaat niet
make[1]: *** [libZeroGSLinux_a-Conf.o] Fout 1
make[1]: Map '/home/wild/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
make: *** [install-recursive] Fout 1
Error with building plugins



hope's are high :)

Have you installed the CG toolkit from nvidia? If yes, [browse here.]("http://www.google.com/search?hl=en&q=%22Error+with+building+plugins%22+pcsx2")

---

### Post by go_beep_yourself on 2007-11-19
> **go_beep_yourself said:**
> What plugins are needed for pcsx2 to work? Are they included with the source code or do I have to download them separately? What can I do about this error?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=49975&d=1194870476[/IMG]

bump!!! What can I do about this to get PCSX2 working??????

---

### Post by hikaricore on 2007-11-19
> **go_beep_yourself said:**
> bump!!! What can I do about this to get PCSX2 working??????

You need to follow the instruction for the previous version on the first page, the latest version will download if you follow those instructions exactly and the compile process should be successful.
Don't bump again until you actually read the howto.

---

### Post by go_beep_yourself on 2007-11-19
> **hikaricore said:**
> You need to follow the instruction for the previous version on the first page, the latest version will download if you follow those instructions exactly and the compile process should be successful.
Don't bump again until you actually read the howto.

Compile process was fine, and I'll bump whenever I feel like it.

---

### Post by go_beep_yourself on 2007-11-19
What makes you assume that I have not read it? Assuming makes an *** out of you and me.

---

### Post by hikaricore on 2007-11-19
> **go_beep_yourself said:**
> Compile process was fine, and I'll bump whenever I feel like it.

No.  Excessive and unnecessary will not be tolerated.  Thanks.

> **go_beep_yourself said:**
> What makes you assume that I have not read it? Assuming makes an *** out of you and me.

I've compiled 0.9.4 on 8 different systems across 3 different version of Ubuntu to date.
One of your plugins in not compiling, hence you missed a library or did not follow the steps properly.

---

### Post by wildnr1 on 2007-11-20
yes I have installed the CG toolkit
on the site you gave I found nothing new
anyone knows more?

---

### Post by go_beep_yourself on 2007-11-20
> **hikaricore said:**
> No.  Excessive and unnecessary will not be tolerated.  Thanks.



I've compiled 0.9.4 on 8 different systems across 3 different version of Ubuntu to date.
One of your plugins in not compiling, hence you missed a library or did not follow the steps properly.

Wrong, I've double checked, and I have all of the libraries.

> **hikaricore said:**
> No.  Excessive and unnecessary will not be tolerated.  Thanks.



I've compiled 0.9.4 on 8 different systems across 3 different version of Ubuntu to date.
One of your plugins in not compiling, hence you missed a library or did not follow the steps properly.

Obviously the directions are not complete. Otherwise, many people here wouldn't be having problems.

---

### Post by go_beep_yourself on 2007-11-20
> **KevNice said:**
> ok, I tried to build this after installing the NVIDIA thing, and it gets pretty far but stops:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-memcpy_amd.o -MD -MP -MF ".deps/libZeroGSogl_a-memcpy_amd.Tpo" -c -o libZeroGSogl_a-memcpy_amd.o `test -f 'memcpy_amd.cpp' || echo './'`memcpy_amd.cpp; \
        then mv -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo" ".deps/libZeroGSogl_a-memcpy_amd.Po"; else rm -f ".deps/libZeroGSogl_a-memcpy_amd.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Regs.o -MD -MP -MF ".deps/libZeroGSogl_a-Regs.Tpo" -c -o libZeroGSogl_a-Regs.o `test -f 'Regs.cpp' || echo './'`Regs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Regs.Tpo" ".deps/libZeroGSogl_a-Regs.Po"; else rm -f ".deps/libZeroGSogl_a-Regs.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-x86.o -MD -MP -MF ".deps/libZeroGSogl_a-x86.Tpo" -c -o libZeroGSogl_a-x86.o `test -f 'x86.cpp' || echo './'`x86.cpp; \
        then mv -f ".deps/libZeroGSogl_a-x86.Tpo" ".deps/libZeroGSogl_a-x86.Po"; else rm -f ".deps/libZeroGSogl_a-x86.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zpipe.o -MD -MP -MF ".deps/libZeroGSogl_a-zpipe.Tpo" -c -o libZeroGSogl_a-zpipe.o `test -f 'zpipe.cpp' || echo './'`zpipe.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zpipe.Tpo" ".deps/libZeroGSogl_a-zpipe.Po"; else rm -f ".deps/libZeroGSogl_a-zpipe.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-Mem.o -MD -MP -MF ".deps/libZeroGSogl_a-Mem.Tpo" -c -o libZeroGSogl_a-Mem.o `test -f 'Mem.cpp' || echo './'`Mem.cpp; \
        then mv -f ".deps/libZeroGSogl_a-Mem.Tpo" ".deps/libZeroGSogl_a-Mem.Po"; else rm -f ".deps/libZeroGSogl_a-Mem.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-rasterfont.o -MD -MP -MF ".deps/libZeroGSogl_a-rasterfont.Tpo" -c -o libZeroGSogl_a-rasterfont.o `test -f 'rasterfont.cpp' || echo './'`rasterfont.cpp; \
        then mv -f ".deps/libZeroGSogl_a-rasterfont.Tpo" ".deps/libZeroGSogl_a-rasterfont.Po"; else rm -f ".deps/libZeroGSogl_a-rasterfont.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-targets.o -MD -MP -MF ".deps/libZeroGSogl_a-targets.Tpo" -c -o libZeroGSogl_a-targets.o `test -f 'targets.cpp' || echo './'`targets.cpp; \
        then mv -f ".deps/libZeroGSogl_a-targets.Tpo" ".deps/libZeroGSogl_a-targets.Po"; else rm -f ".deps/libZeroGSogl_a-targets.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O2 -fomit-frame-pointer  -MT libZeroGSogl_a-zerogs.o -MD -MP -MF ".deps/libZeroGSogl_a-zerogs.Tpo" -c -o libZeroGSogl_a-zerogs.o `test -f 'zerogs.cpp' || echo './'`zerogs.cpp; \
        then mv -f ".deps/libZeroGSogl_a-zerogs.Tpo" ".deps/libZeroGSogl_a-zerogs.Po"; else rm -f ".deps/libZeroGSogl_a-zerogs.Tpo"; exit 1; fi
zerogs.cpp:321: warning: non-local variable ‘<anonymous union> g_vars’ uses anonymous type
zerogs.cpp: In function ‘void ZeroGS::HandleGLError()’:
zerogs.cpp:892: error: ‘GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT’ was not declared in this scope
make[1]: *** [libZeroGSogl_a-zerogs.o] Error 1
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
kevin@kevin-laptop:~/pcsx2$ 


```

any ideas?

Yes, install this package and try again.

libglew1.4-dev

---

### Post by wildnr1 on 2007-11-26
To **go_beep_yourself**'s Avatar  	

yes, the install worked now, thaks a lot
will check it out now but:

[COLOR="Red"]YOUR THE MAN[/COLOR]

---

### Post by x0a on 2007-11-30
I get the following message when I start pcsx2:

First: PCSX2 needs to be configured

But then comes the following message:

Coud not load the plugins/ directory

When I coose the plugin directory manually nothing happens


Need Help...

---

### Post by wishyjr on 2007-11-30
what files are actually in the plugins folder? I don't mean to be insulting or stupid but ive notcied that some pcsx versions files don't actually have the plugin files included.

---

### Post by go_beep_yourself on 2007-11-30
> **wishyjr said:**
> what files are actually in the plugins folder? I don't mean to be insulting or stupid but ive notcied that some pcsx versions files don't actually have the plugin files included.

What plugins should go in the plugin directory? Does installing pcsx2 create a directory with the plugins in it? If yes, where?

---

### Post by KevNice on 2007-12-01
> **go_beep_yourself said:**
> Yes, install this package and try again.

libglew1.4-dev

Ok, I did that, and I got a little farther into the build, but now it stops up here:

```
zerogs.cpp:321: warning: non-local variable ‘<anonymous union> g_vars’ uses anonymous type
zerogs.cpp: In function ‘void ZeroGS::HandleGLError()’:
zerogs.cpp:892: error: ‘GL_FRAMEBUFFER_INCOMPLETE_DUPLICATE_ATTACHMENT_EXT’ was not declared in this scope
make[1]: *** [libZeroGSogl_a-zerogs.o] Error 1
make[1]: Leaving directory `/home/kevin/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins

```

---

### Post by MNICY on 2007-12-02
When i type 'sh build.sh all' i get this:
```
casey@ubuntu:/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
/usr/share/aclocal/oaf.m4:4:   run info '(automake)Extending aclocal'
/usr/share/aclocal/oaf.m4:4:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
autom4te: cannot open autom4te.cache/requests: Permission denied
aclocal: autom4te failed with exit status: 1
/usr/bin/autoconf: 44: cannot create conf18638.sh: Permission denied
/usr/bin/autoconf: 44: cannot create conf18638.sh: Permission denied
chmod: cannot access `conf18638.sh': No such file or directory
autom4te: cannot open autom4te.cache/requests: Permission denied
automake: autoconf failed with exit status: 1
/usr/bin/autoconf: 44: cannot create conf18834.sh: Permission denied
/usr/bin/autoconf: 44: cannot create conf18834.sh: Permission denied
chmod: cannot access `conf18834.sh': No such file or directory
autom4te: cannot open autom4te.cache/requests: Permission denied
chmod: changing permissions of `configure': Operation not permitted
./configure: 53: cannot create conf18899.sh: Permission denied
./configure: 53: cannot create conf18899.sh: Permission denied
chmod: cannot access `conf18899.sh': No such file or directory
./configure: line 44: conf18899.sh: Permission denied
./configure: line 45: conf18899.sh: Permission denied
chmod: cannot access `conf18899.sh': No such file or directory
mkdir: cannot create directory `conf18899.dir': Permission denied
./configure: line 499: conf18899.file: Permission denied
./configure: line 1370: config.log: Permission denied
./configure: line 1380: config.log: Permission denied
Making clean in Linux
make[1]: Entering directory `/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
rm: cannot remove `libZeroGSLinux_a-callbacks.o': Permission denied
make[1]: [mostlyclean-compile] Error 1 (ignored)
make[1]: Leaving directory `/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
Conf.cpp:103: fatal error: opening dependency file .deps/libZeroGSLinux_a-Conf.Tpo: Permission denied
compilation terminated.
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins
```

---

### Post by Sarteck on 2007-12-05
Note to OP,

I had to **sudo apt-get install libglew-dev** as well as what you listed.

---

### Post by PokerFacePenguin on 2007-12-09
> **buttons said:**
> Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").

I'm running Edgy, and I managed to compile the SVN, so here is a mini-howto for compilation.  This is by no means comprehensive, as who knows what -dev packages you might be missing that I've picked up somewhere along the line.

I KNOW it requires:

libbz2-dev
subversion
libjpeg62-dev
build-essential
libgtk2.0-dev
libxxf86vm-dev
x11proto-xf86vidmode-dev
automake1.9
Nvidia Cg-Toolkit (available [HERE]("http://developer.nvidia.com/object/cg_toolkit.html"))

The automake version is important, as it will spit all sorts of errors if you have an earlier version.

It PROBABLY requires:
libglu1-mesa-dev

I can't actually say it needs that for certain, only that I have it and the INSTALL file says you need OpenGL libs in order to compile.

-----------

Okay, so let's grab our required things:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```
Our maybe required things:
```
sudo apt-get install libglu1-mesa-dev
```

The SVN code:

```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```

Aaaand build it!

```
cd pcsx2
sh build.sh all
```

And hopefully everything should build!

EDIT: libbz2-dev is required for the ISO plugins to compile

When I try to build I get the following 
```
oe@tower:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
        then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
        then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
        then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
In file included from GSmain.cpp:39:
zerogs.h:41:19: error: Cg/cg.h: No such file or directory
zerogs.h:42:21: error: Cg/cgGL.h: No such file or directory
zerogs.h:124: error: ‘CGprogram’ does not name a type
zerogs.h:132: error: ‘CGprogram’ does not name a type
zerogs.h:133: error: ‘CGparameter’ does not name a type
zerogs.h:134: error: ‘CGparameter’ does not name a type
zerogs.h:135: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:145: error: ‘CGprogram’ does not name a type
zerogs.h:146: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:182: error: ‘CGparameter’ does not name a type
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/joe/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
```


What kind of plugins do I need.

Also, I do run nvidia and nvidia graphics chipset/vid card ....

How do I install the Nvidia Cg-Toolkit?  

Is there a potential for it to write over anything important that I have already set up?

---

### Post by barius on 2007-12-09
Try this [guide]("http://ubuntuforums.org/showthread.php?t=631979"), it is more up-to-date.  When following it just copy/paste don't try to customize unless you know what you're doing.

---

### Post by PokerFacePenguin on 2007-12-09
Thanks for the tip.  I got it a little further (it compiles, I set up a bios, and I get to set up things with configure), but I still have not gotten my PS2 controller (using a ps3 usb adapter) to work yet.  Unfortunately, I have run out of time this weekend to play with it further until I return from working out of town next week.  If only I could take my beefy home pc with me.....sigh.

---

### Post by go_beep_yourself on 2007-12-12
> **buttons said:**
> Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").


Where are the binaries? I have no plugins after compiling and hikorki just posts some useless crap when I try to get help.

---

### Post by hikaricore on 2007-12-13
You've been pointed at the SVN install instructions before, I don't see the point in doing it again when you won't bother doing what is suggested.

---

### Post by CrinkElite on 2007-12-18
Please please please help i am about to go insane, for the last few days i have been trying to compile and install PCSX2 on my home desktop pc.
I am using Ubuntu Gutsy Gibbon with a core 2 duo e6600  and an Nvidia ge-force 7600 with 2 gigs of ram. 
after many failed attempts i finally got it installed and got as far as the  configuration window which prompts me to assign directories for plugins and the PS2 bios. it has no problems  recognising the bios but  i'm stuck there, i downloaded all the relevant plugin files from the PCSX2 forum 
(who incidentally are not allowing any new members on their pages, hence me bugging you guys) 
   and copy and pasted the different pieces to their correct locations as indicated by their README texts, but when I try to select plugins there are no plugins in the plugin fields to select from, even though i have pointed it to the correct directories. Please If anyone can shed any light it would be greatly appreciated.

---

### Post by barius on 2007-12-18
Delete what you have (except your bios) and follow [this]("http://ubuntuforums.org/showthread.php?t=631979").

---

### Post by CrinkElite on 2007-12-19
thanks man, it actually worked, i could have saved a lot of grief if i had gone there in the first place

---

### Post by Vamp898 on 2008-01-04
I compiled pcsx2 0.9.5 and all worked good. But one problem

[http://img155.imageshack.us/img155/9813/pcsx2zc2.png](http://img155.imageshack.us/img155/9813/pcsx2zc2.png)

---

### Post by Vamp898 on 2008-01-04
i have a Pentium 4 with 3,06 GHz and a GeForce FX Go5600 with 128mb

---

### Post by Kallewoof on 2008-01-04
I've got a dual core 4.4 GHz amd64 machine with 2 GB RAM. I've tried FFX and it's super-laggy.

I've read through this entire thread and done what people suggest. 
[LIST]
[*]I didn't have the GL_SYNC_TO_VBLANK set (checked nvidia-config).
[*]I have all the options in the CPU configuration checked.
[*]I compiled from the latest SVN sources. 
[*] I don't have beryl/compiz enabled.
[/LIST]

I've read that Pete's MesaGL drivers work best, but those aren't available for amd64... any ideas what I can do to speed this up?

-Kalle.

---

### Post by liquidypoo on 2008-01-04
Everything has compiled and I assume the program works fine and all, considering I was able to map my buttons to my USB controller and everything, but I can't run any games.  When I click Run CD, a message box pops up saying "Error Opening GS Plugin."

Help?

---

### Post by barius on 2008-01-07
> **Kallewoof said:**
> I've got a dual core 4.4 GHz amd64 machine with 2 GB RAM. I've tried FFX and it's super-laggy.

-Kalle.

I think you mean that you have an AMD64 X2 4400+ processor.  FYI, these CPUs do not run at 4400Ghz, that's just a model number.  The 4400 runs at 2.3Ghz.  The model number is a rough guess-timation of their power when compared to an Intel Pentium 4 class processor.  Further, the P4 is Intel's old model that is no longer being produced.  The current model is known as Core 2 Duo, and it is *much* faster per-clock.  In summary, the 4400 model number is just a marketing tool.

I think there are two reasons FFX seems slow to you:

1 - The bottom line is that PCSX2 requires a *very* powerful machine to emulate any 3D game at full speed.  Some games cannot even be emulated at full speed on the newest and most powerful gaming rigs that can be bought today.  Your CPU is simply not powerful enough to emulate FFX at 60fps.  Heck, even my rig with an Intel C2D E6600 overclocked to 3Ghz (from 2.4Ghz) does not run FFX at full speed all the time.

2 - Frame rate (fps) in PCSX2 does not work the same as it does on PC games.  If your frame rate in PCSX2 is 30fps then the game will actually be running at *half* the speed it would on a PS2 and will appear to be moving in s-l-o-w m-o-t-i-o-n.  In order to have full speed you must get 60fps (NTSC, 50 if PAL).  If you want more explanation I suggest searching for past posts on the PCSX2 forums as this question comes up quite often.  I don't suggest asking it again, you'll likely get flamed by all the users who are tired of hearing it.

---

### Post by barius on 2008-01-07
> **liquidypoo said:**
> Everything has compiled and I assume the program works fine and all, considering I was able to map my buttons to my USB controller and everything, but I can't run any games.  When I click Run CD, a message box pops up saying "Error Opening GS Plugin."

Help?

Have you configured all your plugins?  Was one or more GS plugins listed?  If so, try the PCSX2 forums (pcsx2.net->forums).

If no plugin is listed, then it didn't compile.  Delete what you have, except your bios, and follow my [guide.]("http://ubuntuforums.org/showthread.php?t=631979")  Just copy/paste the code blocks into a terminal and it will do everything for you.

---

### Post by Kallewoof on 2008-01-07
Barius,

Thanks for the reply, but you've confused me thoroughly. Firstly.

> **barius said:**
> I think you mean that you have an AMD64 X2 4400+ processor.  FYI, these CPUs do not run at 4400Ghz, that's just a model number.  The 4400 runs at 2.3Ghz.

> 
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
[...]
cpu MHz         : 2211.357
[...]
processor       : 1
vendor_id       : AuthenticAMD
[...]
cpu MHz         : 2211.357


2211.357 + 2211.357 = 4422.714 MHz = 4.4 GHz. Not sure how else you would interpret it. Unless you meant that by "dual core 4.4 GHz" one'd expect 2 x 4.4 GHz = 8.8 GHz total. I guess that's a matter of interpretation and in that case you're right that it's a marketing tool only.

> I think there are two reasons FFX seems slow to you:

1 - The bottom line is that PCSX2 requires a *very* powerful machine to emulate any 3D game at full speed.  Some games cannot even be emulated at full speed on the newest and most powerful gaming rigs that can be bought today.  Your CPU is simply not powerful enough to emulate FFX at 60fps.  Heck, even my rig with an Intel C2D E6600 overclocked to 3Ghz (from 2.4Ghz) does not run FFX at full speed all the time.

This is the part where I get confused. Lots of people quote hardware that is equal or less to what I have and claim it should or does play FFX fine. By "fine" I presumed they didn't mean the game went at 0.1x :)

> 
2 - Frame rate (fps) in PCSX2 does not work the same as it does on PC games.  If your frame rate in PCSX2 is 30fps then the game will actually be running at *half* the speed it would on a PS2 and will appear to be moving in s-l-o-w m-o-t-i-o-n.  In order to have full speed you must get 60fps (NTSC, 50 if PAL).  If you want more explanation I suggest searching for past posts on the PCSX2 forums as this question comes up quite often.  I don't suggest asking it again, you'll likely get flamed by all the users who are tired of hearing it.

Ahh, didn't know that (frame rate deal). As for getting flamed, I guess that's a chance you have to take whenever you post anywhere. I read through the whole thread and tried everything I could see and by the nature of replies to other posters it didn't seem like anyone got flamed. Unless they were being idiotic. :)

I'll look at the PCSX2 forums. Thanks for taking the time.

-Kalle.

---

### Post by barius on 2008-01-07
> **Kallewoof said:**
> 
2211.357 + 2211.357 = 4422.714 MHz = 4.4 GHz. Not sure how else you would interpret it. Unless you meant that by "dual core 4.4 GHz" one'd expect 2 x 4.4 GHz = 8.8 GHz total. I guess that's a matter of interpretation and in that case you're right that it's a marketing tool only.


That is an interesting coincidence, I hadn't noticed it before.  I am quite sure, however, that the numbers are references to Intels' Ghz numbers.  AMD spent years trying to get consumers to understand that those numbers are meaningless (I won't go into details), but in the end they gave up on the high road and just started labeling their models in such a way as to make them look equivalent or better to Intel's models.  The fact is, those numbers are only marginally meaningful when compared to the Intel Pentium 4 architecture, which was surpassed years ago by newer models.  The Intel C2D is roughly 40% faster per-clock than an AMD X2 when playing PCSX2.  Keep in mind though that other applications aren't likely to see quite that much of a difference, but from various benchmarks I'd guesstimate the C2D is about 20% faster per-clock on average.

> **Kallewoof said:**
> 
This is the part where I get confused. Lots of people quote hardware that is equal or less to what I have and claim it should or does play FFX fine. By "fine" I presumed they didn't mean the game went at 0.1x :)


Most likely their idea of 'fine' is simply to play the game at half speed.  I got about 1/4 thru FFX on my old machine running at 20fps and it was still pretty fun.  However, if you're trying to enjoy a game for the first time you'll get the best experience from your PS2.

There's another possibility though, it is more than likely at least some of them were overclocking their CPUs.  FYI, 'overclocking' is when you turn up the clock speed of your CPU by using tools included in most PC BIOSes.  The Intel C2D is known to 'oc' significantly with little effort, so an E6300 can often be oc'd from 1.8Ghz all the way to 3.0Ghz (+1.2), practically doubling it's speed for free.  The AMD64 X2 series can also oc a fair amount, but not nearly as much as the C2D.  The most common oc I've seen for your CPU is about 2.8Ghz (+0.6).

You'll find that most of the 'power users' on the PCSX2 forums are avid oc'ers.  This is why some of them seem to get amazing speeds.  If you don't know what oc'ing is, then don't try it until you read a few guides because you can damage your hardware.

---

### Post by KhaaL on 2008-01-09
Is there any chance that we might see PCSX2 & plugins to run games released as .debs? I've tried compiling it and my hair turned grey in the (failing) process.

---

### Post by Kallewoof on 2008-01-10
Thanks a lot for taking the time to clarify, barius!

-Kalle.

---

### Post by absolutezero1287 on 2008-01-21
I ran into a bit of trouble when I did this.

Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?               no
  SSE2 enabled?            yes
Making clean in Linux
make[1]: Entering directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
        then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
        then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/leonardo/Desktop/Pcsx2_0.9.4_Source/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

---

### Post by blacksm1th on 2008-01-28
> **absolutezero1287 said:**
> ...
Install from Synaptic this - libglew1.4-dev

---

### Post by GSF1200S on 2008-02-03
Well, I got 0.9.4 running according to this howto, but it says it needs to be configured and complains that it cannot find the /plugins and /bios- any ideas?

---

### Post by brokenhachi on 2008-02-07
> Entering directory `/home/dave/Desktop/pcs/pcsx2/Linux'
test -z "/home/dave/Desktop/pcs/bin" || mkdir -p -- "/home/dave/Desktop/pcs/bin"
  /usr/bin/install -c 'pcsx2' '/home/dave/Desktop/pcs/bin/pcsx2'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dave/Desktop/pcs/pcsx2/Linux'
make[1]: Leaving directory `/home/dave/Desktop/pcs/pcsx2/Linux'



thats the last lines of the error that i get when installing... can someone help?

---

### Post by gigaferz on 2008-02-07
I found a deb package for pcsx2 @ getdeb

 I installed it but I experienced an error because i have no graphics card

[http://www.getdeb.net/app/PCSX2](http://www.getdeb.net/app/PCSX2)

---

### Post by someoneouthere on 2008-02-19
> **buttons said:**
> Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").

I'm running Edgy, and I managed to compile the SVN, so here is a mini-howto for compilation.  This is by no means comprehensive, as who knows what -dev packages you might be missing that I've picked up somewhere along the line.

I KNOW it requires:

libbz2-dev
subversion
libjpeg62-dev
build-essential
libgtk2.0-dev
libxxf86vm-dev
x11proto-xf86vidmode-dev
automake1.9
Nvidia Cg-Toolkit (available [HERE]("http://developer.nvidia.com/object/cg_toolkit.html"))

The automake version is important, as it will spit all sorts of errors if you have an earlier version.

It PROBABLY requires:
libglu1-mesa-dev

I can't actually say it needs that for certain, only that I have it and the INSTALL file says you need OpenGL libs in order to compile.

-----------

Okay, so let's grab our required things:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```
Our maybe required things:
```
sudo apt-get install libglu1-mesa-dev
```

The SVN code:

```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```

Aaaand build it!

```
cd pcsx2
sh build.sh all
```

And hopefully everything should build!

EDIT: libbz2-dev is required for the ISO plugins to compile

how can i unistall everthing? is there a script or something?

---

### Post by Zzzach on 2008-02-19
I don't get the point of this if it can't run any games :confused: You can buy a ps2 for like $100.

---

### Post by kanem on 2008-02-20
> **Zzzach said:**
> I don't get the point of this if it can't run any games :confused: You can buy a ps2 for like $100.
PS2s won't be around forever. I still play Genesis games sometimes on an emulator, so I imagine ten years from now I'll still want to play some PS2 games.

As for why do this now; I'd rather play PS2 games on my laptop, which is portable, than my PS2, which is not.

---

### Post by fain on 2008-02-25
> **kanem said:**
> PS2s won't be around forever.

yes i haven't seen a ps2 last more than 2 years yet. they really skimped on the parts for that thing.

and ill take free over paying 100 dollars any day.

---

### Post by GSZX1337 on 2008-02-25
> **fain said:**
> yes i haven't seen a ps2 last more than 2 years yet. they really skimped on the parts for that thing.

and ill take free over paying 100 dollars any day.

My PS2 has lasted for seven years and counting. I also have never gotten the dreaded "Disc Read Failure" error unless the disc was broken or dirty. ;)

---

### Post by Yayzik on 2008-06-04
I'm sorry, I'm terribly frustrated over this, and I'm rather new--how do I wipe everything I've done so far (I encountered an error at the sh build.sh all step) and start fresh (with Barius's guide)?

---

### Post by the_bloods_city on 2008-06-12
after sh build.sh all
give me this
```
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

```
i install every thing and install nvidia cg

---

### Post by Nazty_Nayt on 2008-06-21
I get the same error as bloods, whenever I try to run CD, I get an error saying ZeroSPU2: Failed to initialize sound.

Can someone help me I've practically spent all day trying to find a solution to this problem, and nothing is working.

---

### Post by ucal on 2008-06-21
Awesome.  Now I can play both Frets on Fire and GH3.  Just need to get a USB adapter.  

:guitar:

---

### Post by PatronSaint on 2008-06-26
> **Nazty_Nayt said:**
> I get the same error as bloods, whenever I try to run CD, I get an error saying ZeroSPU2: Failed to initialize sound.

Can someone help me I've practically spent all day trying to find a solution to this problem, and nothing is working.

I get the same thing as well...I have NO IDEA how to fix this stuff.

---

### Post by equity on 2008-06-29
Btw what is the newest BIOS version?

---

### Post by devfil on 2008-07-10
> **the_bloods_city said:**
> after sh build.sh all
give me this
```
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/x-man/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

```
i install every thing and install nvidia cg
sudo apt-get install libglew1.5-dev

---

### Post by IamJohnHayes on 2008-07-12
same problem as above.  and the package devfil suggested does not exist.

---

### Post by devfil on 2008-07-12
> **IamJohnHayes said:**
> same problem as above.  and the package devfil suggested does not exist.
Are you sure about this?
[http://packages.ubuntu.com/hardy/libglew1.5-dev](http://packages.ubuntu.com/hardy/libglew1.5-dev)
However try to install libglew-dev package.

---

### Post by IamJohnHayes on 2008-07-12
I have gutsy which i guess (I am still pretty much a noob here) is why i did see it.

---

### Post by devfil on 2008-07-13
> **IamJohnHayes said:**
> I have gutsy which i guess (I am still pretty much a noob here) is why i did see it.

If you are using gutsy, install libglew1.4-dev package.

---

### Post by Aardolan on 2008-07-16
There's a deb file for PCSX2, I found it through Google. Both 32 and 64 bit versions.
[http://linux.softpedia.com/progDownload/PCSX2-Download-2079.html](http://linux.softpedia.com/progDownload/PCSX2-Download-2079.html) is where I got it. However, I don't know how to configure it correctly, and don't have a joypad that I know will work with linux, so I haven't tested it out yet :/

---

### Post by javagamer on 2008-07-21
sudo apt-get install libglew1.5-dev worked for me.  Thanks a bunch.

---

### Post by Ningen on 2008-08-16
I get the error "Error with building plugins" How do I fix this?

---

### Post by desertboy on 2008-08-17
> **GSZX1337 said:**
> My PS2 has lasted for seven years and counting. I also have never gotten the dreaded "Disc Read Failure" error unless the disc was broken or dirty. ;)

Me and my friend bought our Ps2's on the same day from the same shop not long after they came out in the UK, his went wrong 1 year and 1 day after he bought it with the disc read error, mine still works now, go figure.

Mind you my PSX still works

---

### Post by lubosz on 2008-09-12
[http://brainstorm.ubuntu.com/idea/13110/](http://brainstorm.ubuntu.com/idea/13110/)

---

### Post by -siGGi- on 2008-12-09
PCSX2 Repo:

Hardy:
```
echo "deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install pcsx2
```

Source:
[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by Vvar hero on 2008-12-15
i am lost :( i need help with my pcsx

---

### Post by Maheriano on 2008-12-15
Sorry but......what is this for?

---

### Post by hikaricore on 2008-12-15
> **Maheriano said:**
> Sorry but......what is this for?

This is a thread for PCSX2 one of the better PS2 emulators out there.

---

### Post by Maheriano on 2008-12-15
Sorry for the hijack but am I reading this right? There's an emulator for the Playstation 2 now? Are all the ROM available? Can I throw my PS2 in the trash and just use this?

---

### Post by hikaricore on 2008-12-15
There have been PS2 emulators for years.

**We will not be discussing "roms" on this forum now or ever.**

If you have existing PS2 titles you may be able to play them with this emulator.

In most cases of emulation nothing will ever replace the original, you'd have to be insane to throw a perfectly good game console away for an emu.

---

### Post by Maheriano on 2008-12-15
Sorry, just wanted to make sure it worked as well without any major problems. I must be behind the times, my first time hearing of this. Carry on.

---

### Post by k4rizma on 2008-12-20
What do I do with the CG toolkit after i've downloaded it? 

thanks!

---

### Post by Maheriano on 2008-12-21
Didn't build. I followed everything you typed there, what happened?

```

deemar@Chugger:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/deemar/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins
deemar@Chugger:~/pcsx2$ 

```

---

### Post by Perfect Storm on 2008-12-21
You forgot to install the -dev package of libglew


If you read the output error.
The first indications
> checking for main in -lGLEW... no
the next
> ../GS.h:41:21: error: GL/glew.h: No such file or directory

---

### Post by Maheriano on 2008-12-22
> **Artificial Intelligence said:**
> You forgot to install the -dev package of libglew


If you read the output error.
The first indications

the next

I ran this from the first post, where does it mention installing libglew?

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```

It's just that I don't see this as required anywhere on the first page of this thread so I'm confused. How do I get it? Do I use apt-get? Sorry I'm clueless.

---

### Post by Perfect Storm on 2008-12-22
The thread is old.

Easist is to search synaptic for glew or libglew. When compiling something against this (or other libs) you need the -dev version.

but here you go (ubuntu 8.10);
```
sudo apt-get install libglew1.5-dev
```

See if it helps.

---

### Post by lazcisco on 2009-01-07
I'm getting the following error, any clue how to fix it?

```

mie@me-laptop:~/pcsx2$ sh build.sh install
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Making install in Linux
make[1]: Entering directory `/home/me/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Entering directory `/home/me/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/me/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/me/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/me/pcsx2/plugins/gs/zerogs/opengl'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer   -g -O2  -DZEROGS_SSE2 -MT libZeroGSogl_a-x86-32.o -MD -MP -MF .deps/libZeroGSogl_a-x86-32.Tpo -c -o libZeroGSogl_a-x86-32.o `test -f 'x86-32.S' || echo './'`x86-32.S
x86-32.S: Assembler messages:
x86-32.S:825: Error: ambiguous operand size or operands invalid for `movdqa'
x86-32.S:826: Error: ambiguous operand size or operands invalid for `movdqa'
x86-32.S:827: Error: ambiguous operand size or operands invalid for `movdqa'
x86-32.S:828: Error: ambiguous operand size or operands invalid for `movdqa'
make[1]: *** [libZeroGSogl_a-x86-32.o] Error 1
make[1]: Leaving directory `/home/me/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins


```

---

### Post by cristianrosa on 2009-02-23
Use the SVN version, the revision 396 includes changes for gcc 4.3.2

From the change log of the SVN:

> fixes for gcc 4.3.2. Gcc now checks the argument pointer size for mmx instructions in intel mode. It never used to so movq with incorrect xmmword pointer arguments were allowed. With 4.3.2, these need to be corrected to qword.

---

### Post by Indian_Guy101 on 2009-03-19
I can compile it fine but how do I start up a game? (I have a bios and I am pretty sure I configured the plugins right)

---

### Post by psycho45 on 2009-03-20
I was playing ff9 and switching to a new disk when i accidently pressed F1 in the starting screen, which pretty much erased all my hard work. is there any way to retrieve a previous previous save state? i'm reallllllly hoping i don't have to start completely over... T_T someone help!

---

### Post by hikaricore on 2009-03-20
> **psycho45 said:**
> I was playing ff9 and switching to a new disk when i accidently pressed F1 in the starting screen, which pretty much erased all my hard work. is there any way to retrieve a previous previous save state? i'm reallllllly hoping i don't have to start completely over... T_T someone help!

Not really, is there something wrong with saving your progress with the memory card functionality?
If you've done this you shouldn't have too much to redo.

---

### Post by Sadaiyappan on 2009-03-21
I compiled the from the svn like the directions in the first post said too do.   Now I don't know how to start the program.  When I look in the folder there is no program there that starts pcsx2.. Please help!

---

### Post by GSF1200S on 2009-03-21
> **Sadaiyappan said:**
> I compiled the from the svn like the directions in the first post said too do.   Now I don't know how to start the program.  When I look in the folder there is no program there that starts pcsx2.. Please help!

If I remember correctly, and it has been a long time since I messed with it, you open a terminal and type:

```
pcsx2
```

---

### Post by urd on 2009-04-02
> **buttons said:**
> Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").

I'm running Edgy, and I managed to compile the SVN, so here is a mini-howto for compilation.  This is by no means comprehensive, as who knows what -dev packages you might be missing that I've picked up somewhere along the line.

I KNOW it requires:

libbz2-dev
subversion
libjpeg62-dev
build-essential
libgtk2.0-dev
libxxf86vm-dev
x11proto-xf86vidmode-dev
automake1.9
Nvidia Cg-Toolkit (available [HERE]("http://developer.nvidia.com/object/cg_toolkit.html"))

The automake version is important, as it will spit all sorts of errors if you have an earlier version.

It PROBABLY requires:
libglu1-mesa-dev

I can't actually say it needs that for certain, only that I have it and the INSTALL file says you need OpenGL libs in order to compile.

-----------

Okay, so let's grab our required things:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```
Our maybe required things:
```
sudo apt-get install libglu1-mesa-dev
```

The SVN code:

```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```

Aaaand build it!

```
cd pcsx2
sh build.sh all
```

And hopefully everything should build!

EDIT: libbz2-dev is required for the ISO plugins to compile


the nvidia toolkit its necesary for ati cards too??? i didn't install it because i don't know if i need that for ati cards too ... this the result

```
urd@urd-laptop:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
/usr/share/aclocal/snacc.m4:24: warning: underquoted definition of AM_PATH_SNACC
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... no
checking for GL/glu.h... no
checking for GL/glext.h... no
checking for main in -lGL... yes
checking for main in -lGLU... no
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
../GS.h:42:19: error: GL/gl.h: No such file or directory
../GS.h:43:20: error: GL/glx.h: No such file or directory
In file included from Conf.cpp:25:
../GS.h:110: error: &#8216;GLXContext&#8217; does not name a type
Conf.cpp: In function &#8216;void LoadConfig()&#8217;:
Conf.cpp:66: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

```

if is the toolkit how i install it??

---

### Post by urd on 2009-04-03
sorry for the bump, but i need some help :S ... i  alredy installed the toolkit and the error list was huge, and i don't know what to do

```
../gzipv2.c:709: warning: pointer targets in assignment differ in signedness
../gzipv2.c:747: warning: pointer targets in assignment differ in signedness
../gzipv2.c: In function ‘GZipV2Write’:
../gzipv2.c:851: warning: pointer targets in passing argument 1 of ‘compress2’ differ in signedness
../gzipv2.c:851: warning: pointer targets in passing argument 3 of ‘compress2’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../ecma119.c -o ../ecma119.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../bzip2v3.c -o ../bzip2v3.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../bzip2v2.c -o ../bzip2v2.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../toc.c -o ../toc.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../ini.c -o ../ini.o
rm -f libCDVDisoEFP.so
gcc -shared -Wl,-soname,libCDVDisoEFP.so -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -lz -lbz2 \
    CDVDiso.o ../version.o actualfile.o ../isofile.o conf.o logfile.o ../imagetype.o ../multifile.o ../isocompress.o ../convert.o ../gzipv1.o ../blockv2.o ../gzipv2.o  ../ecma119.o ../bzip2v3.o ../bzip2v2.o ../toc.o ../ini.o -o libCDVDisoEFP.so
strip --strip-unneeded --strip-debug libCDVDisoEFP.so
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c interface.c -o interface.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c aboutbox.c -o aboutbox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c mainbox.c -o mainbox.o
mainbox.c: In function ‘MainBoxOKEvent’:
mainbox.c:347: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
mainbox.c: In function ‘MainBoxDisplay’:
mainbox.c:645: warning: pointer targets in passing argument 2 of ‘gtk_entry_set_text’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c selectionbox.c -o selectionbox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c devicebox.c -o devicebox.o
devicebox.c: In function ‘DeviceBoxOKEvent’:
devicebox.c:395: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
devicebox.c:535: warning: pointer targets in passing argument 2 of ‘IsoFileWrite’ differ in signedness
devicebox.c: In function ‘DeviceBoxDisplay’:
devicebox.c:879: warning: pointer targets in passing argument 2 of ‘gtk_entry_set_text’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c conversionbox.c -o conversionbox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c progressbox.c -o progressbox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c messagebox.c -o messagebox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c tablerebuild.c -o tablerebuild.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c device.c -o device.o
device.c: In function ‘DeviceOpen’:
device.c:126: warning: pointer targets in passing argument 1 of ‘open’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c CD.c -o CD.o
CD.c:77: warning: pointer targets in initialization differ in signedness
CD.c:79: warning: pointer targets in initialization differ in signedness
CD.c: In function ‘CDreadTrack’:
CD.c:151: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
CD.c: In function ‘CDgetDiskType’:
CD.c:649: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
CD.c:693: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c DVD.c -o DVD.o
DVD.c:77: warning: pointer targets in initialization differ in signedness
rm -f cfgCDVDisoEFP
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -lz -lbz2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   \
    interface.o aboutbox.o mainbox.o selectionbox.o devicebox.o conversionbox.o progressbox.o messagebox.o tablerebuild.o device.o CD.o DVD.o ../version.o actualfile.o ../isofile.o conf.o logfile.o ../imagetype.o ../multifile.o ../isocompress.o ../convert.o ../gzipv1.o ../blockv2.o ../gzipv2.o  ../ecma119.o ../bzip2v3.o ../bzip2v2.o ../toc.o ../ini.o -o cfgCDVDisoEFP
strip cfgCDVDisoEFP
------------------
Building CDVDlinuz
------------------
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c CDVDlinuz.c -o CDVDlinuz.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../buffer.c -o ../buffer.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c actualfile.c -o actualfile.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c conf.c -o conf.o
conf.c: In function ‘ExecCfg’:
conf.c:80: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
conf.c: In function ‘LoadConf’:
conf.c:169: warning: pointer targets in passing argument 4 of ‘INILoadString’ differ in signedness
conf.c:171: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
conf.c: In function ‘SaveConf’:
conf.c:183: warning: pointer targets in passing argument 4 of ‘INISaveString’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c logfile.c -o logfile.o
logfile.c: In function ‘PrintLog’:
logfile.c:173: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
logfile.c:175: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c device.c -o device.o
device.c: In function ‘DeviceOpen’:
device.c:133: warning: pointer targets in passing argument 1 of ‘open’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c CD.c -o CD.o
CD.c:77: warning: pointer targets in initialization differ in signedness
CD.c:79: warning: pointer targets in initialization differ in signedness
CD.c: In function ‘CDreadTrack’:
CD.c:151: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
CD.c: In function ‘CDgetDiskType’:
CD.c:649: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
CD.c:693: warning: pointer targets in passing argument 2 of ‘LBAtoMSF’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c DVD.c -o DVD.o
DVD.c:41: warning: pointer targets in initialization differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../convert.c -o ../convert.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../ini.c -o ../ini.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -c ../version.c -o ../version.o
gcc -shared -Wl,-soname,libCDVDlinuz.so -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux  \
    CDVDlinuz.o ../buffer.o actualfile.o conf.o logfile.o device.o CD.o DVD.o ../convert.o ../ini.o ../version.o -o libCDVDlinuz.so
strip --strip-unneeded --strip-debug libCDVDlinuz.so
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c aboutbox.c -o aboutbox.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c mainbox.c -o mainbox.o
mainbox.c: In function ‘MainBoxOKEvent’:
mainbox.c:219: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
mainbox.c: In function ‘MainBoxDisplay’:
mainbox.c:371: warning: pointer targets in passing argument 2 of ‘gtk_entry_set_text’ differ in signedness
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c interface.c -o interface.o
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   \
    aboutbox.o mainbox.o interface.o actualfile.o conf.o logfile.o device.o CD.o DVD.o ../convert.o ../ini.o ../version.o -o cfgCDVDlinuz
strip cfgCDVDlinuz
-----------------
Building CDVDnull
-----------------
gcc -Wall -O2 -fomit-frame-pointer -finline-functions -ffast-math -fno-strict-aliasing -I. -I/usr/local/include -DENABLE_NLS -DPACKAGE=\"pcsx2\" -fPIC -c -o CDVD.o CDVD.c -MD -MF CDVD.d
gcc -shared -Wl,-soname,libCDVDnull.so -Wall -O2 -fomit-frame-pointer -finline-functions -ffast-math -fno-strict-aliasing -I. -I/usr/local/include -DENABLE_NLS -DPACKAGE=\"pcsx2\" -fPIC CDVD.o -o libCDVDnull.so
strip libCDVDnull.so
------------------------
Building DEV9 plugins...
------------------------
Building dev9null...
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D__LINUX__ -c -o dev9null.o dev9null.c -MD -MF dev9null.d
dev9null.c: In function ‘DEV9open’:
dev9null.c:80: warning: unused variable ‘dsp’
rm -f libDEV9null.so
gcc -shared -Wl,-soname,libDEV9null.so -fPIC -Wall -O2 -fomit-frame-pointer -D__LINUX__ dev9null.o -o libDEV9null.so
strip --strip-unneeded --strip-debug libDEV9null.so
----------------------------
Building FireWire plugins...
----------------------------
---------------
Building FWnull
---------------
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o ../FW.o ../FW.c -MD -MF ../FW.d
../FW.c: In function ‘FWopen’:
../FW.c:91: warning: unused variable ‘dsp’
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o Linux.o Linux.c -MD -MF Linux.d
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o Config.o Config.c -MD -MF Config.d
rm -f libFWnull.so
gcc -shared -Wl,-soname,libFWnull.so -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ ../FW.o Linux.o Config.o -o libFWnull.so -lpthread
strip --strip-unneeded --strip-debug libFWnull.so
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o conf.o conf.c -MD -MF conf.d
conf.c: In function ‘OnConf_Ok’:
conf.c:96: warning: unused variable ‘str’
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o interface.o interface.c -MD -MF interface.d
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ -c -o support.o support.c -MD -MF support.d
rm -f cfgFWnull
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -D__LINUX__ conf.o interface.o support.o Config.o -o cfgFWnull -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
strip cfgFWnull
-----------------------
Building PAD plugins...
-----------------------
----------------
Building ZeroPAD
----------------
/usr/share/aclocal/snacc.m4:24: warning: underquoted definition of AM_PATH_SNACC
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
Makefile.am: installing `./compile'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for a x86-64 CPU... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for SDL_Init in -lSDL... no
checking gtk2+... checking for pkg-config... pkg-config
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
checking for main in -lstdc++... yes
checking for main in -ldl... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
Configuration:
  Debug build?           no
  x86-64 build?           no
test -z "libZeroPAD.a" || rm -f libZeroPAD.a
test -z "libZeroPAD.so.0.2.0" || rm -f libZeroPAD.so.0.2.0
rm -f *.o
if gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -I. -I.    -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -O2 -fomit-frame-pointer   -MT libZeroPAD_a-zeropad.o -MD -MP -MF ".deps/libZeroPAD_a-zeropad.Tpo" -c -o libZeroPAD_a-zeropad.o `test -f 'zeropad.cpp' || echo './'`zeropad.cpp; \
    then mv -f ".deps/libZeroPAD_a-zeropad.Tpo" ".deps/libZeroPAD_a-zeropad.Po"; else rm -f ".deps/libZeroPAD_a-zeropad.Tpo"; exit 1; fi
zeropad.cpp:34: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘s32 PADinit(u32)’:
zeropad.cpp:168: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp:177: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result
zeropad.cpp: In function ‘u8 PADstartPoll(int)’:
zeropad.cpp:251: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 _PADpoll(u8)’:
zeropad.cpp:265: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp:400: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 PADpoll(u8)’:
zeropad.cpp:470: warning: deprecated conversion from string constant to ‘char*’
if gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -I. -I.    -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -O2 -fomit-frame-pointer   -MT libZeroPAD_a-linux.o -MD -MP -MF ".deps/libZeroPAD_a-linux.Tpo" -c -o libZeroPAD_a-linux.o `test -f 'Linux/linux.cpp' || echo './'`Linux/linux.cpp; \
    then mv -f ".deps/libZeroPAD_a-linux.Tpo" ".deps/libZeroPAD_a-linux.Po"; else rm -f ".deps/libZeroPAD_a-linux.Tpo"; exit 1; fi
Linux/linux.cpp:25:21: error: SDL/SDL.h: No such file or directory
Linux/linux.cpp:71: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:71: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:74: error: expected `;' before ‘private’
Linux/linux.cpp:85: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:85: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp: In function ‘void LoadConfig()’:
Linux/linux.cpp:163: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp:166: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp:167: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp: In function ‘void PADupdate(int)’:
Linux/linux.cpp:319: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:328: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:328: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:340: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:340: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp:344: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:353: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:362: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:371: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:388: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:388: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp: In function ‘void UpdateConf(int)’:
Linux/linux.cpp:437: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp:441: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp:445: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp: In function ‘void OnConf_Key(GtkButton*, void*)’:
Linux/linux.cpp:499: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:525: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:525: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:542: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:542: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp:546: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:553: error: ‘abs’ was not declared in this scope
Linux/linux.cpp: In static member function ‘static void JoystickInfo::EnumerateJoysticks(std::vector<JoystickInfo*, std::allocator<JoystickInfo*> >&)’:
Linux/linux.cpp:717: error: ‘SDL_INIT_JOYSTICK’ was not declared in this scope
Linux/linux.cpp:717: error: ‘SDL_Init’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_QUERY’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_JoystickEventState’ was not declared in this scope
Linux/linux.cpp:726: error: ‘SDL_NumJoysticks’ was not declared in this scope
Linux/linux.cpp: In constructor ‘JoystickInfo::JoystickInfo()’:
Linux/linux.cpp:753: error: ‘joy’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::Destroy()’:
Linux/linux.cpp:764: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:765: error: ‘SDL_JoystickOpened’ was not declared in this scope
Linux/linux.cpp:766: error: ‘SDL_JoystickClose’ was not declared in this scope
Linux/linux.cpp: In member function ‘bool JoystickInfo::Init(int, bool)’:
Linux/linux.cpp:778: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:778: error: ‘SDL_JoystickOpen’ was not declared in this scope
Linux/linux.cpp:784: error: ‘SDL_JoystickNumAxes’ was not declared in this scope
Linux/linux.cpp:785: error: ‘SDL_JoystickNumButtons’ was not declared in this scope
Linux/linux.cpp:786: error: ‘SDL_JoystickNumHats’ was not declared in this scope
Linux/linux.cpp:787: error: ‘SDL_JoystickName’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::SaveState()’:
Linux/linux.cpp:821: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:821: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:823: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:823: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
make: *** [libZeroPAD_a-linux.o] Error 1
Error with building plugins

```

if someone can help me, i will aprecited a lot :)

thanks

---

### Post by Grishka on 2009-04-03
> **urd said:**
> sorry for the bump, but i need some help :S ... i  alredy installed the toolkit and the error list was huge, and i don't know what to do

<SNIP>

if someone can help me, i will aprecited a lot :)

thanks

you don't have sdl development libraries installed. search for libsdl in synaptic, and install all dev packages.

---

### Post by urd on 2009-04-03
ey man thanks i alredy tryit, but i don't know if is ok ... 
```
Mpeg.c:956: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
Mpeg.c:957: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
rm -f libmpeg2IPU.a
ar cru libmpeg2IPU.a Idct.o Mpeg.o 
ranlib libmpeg2IPU.a
make[3]: Entering directory `/home/urd/pcsx2/pcsx2/IPU/mpeg2lib'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/urd/pcsx2/pcsx2/IPU/mpeg2lib'
make[2]: Leaving directory `/home/urd/pcsx2/pcsx2/IPU/mpeg2lib'
make[2]: Entering directory `/home/urd/pcsx2/pcsx2/IPU'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../ -I./../x86  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT IPU.o -MD -MP -MF ".deps/IPU.Tpo" -c -o IPU.o IPU.c; \
	then mv -f ".deps/IPU.Tpo" ".deps/IPU.Po"; else rm -f ".deps/IPU.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../ -I./../x86  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT yuv2rgb.o -MD -MP -MF ".deps/yuv2rgb.Tpo" -c -o yuv2rgb.o yuv2rgb.c; \
	then mv -f ".deps/yuv2rgb.Tpo" ".deps/yuv2rgb.Po"; else rm -f ".deps/yuv2rgb.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../ -I./../x86  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT coroutine.o -MD -MP -MF ".deps/coroutine.Tpo" -c -o coroutine.o coroutine.c; \
	then mv -f ".deps/coroutine.Tpo" ".deps/coroutine.Po"; else rm -f ".deps/coroutine.Tpo"; exit 1; fi
gcc   -c acoroutine.S
rm -f libIPU.a
ar cru libIPU.a IPU.o yuv2rgb.o coroutine.o acoroutine.o 
ranlib libIPU.a
make[3]: Entering directory `/home/urd/pcsx2/pcsx2/IPU'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/urd/pcsx2/pcsx2/IPU'
make[2]: Leaving directory `/home/urd/pcsx2/pcsx2/IPU'
make[1]: Leaving directory `/home/urd/pcsx2/pcsx2/IPU'
Making install in RDebug
make[1]: Entering directory `/home/urd/pcsx2/pcsx2/RDebug'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2.o -MD -MP -MF ".deps/deci2.Tpo" -c -o deci2.o deci2.c; \
	then mv -f ".deps/deci2.Tpo" ".deps/deci2.Po"; else rm -f ".deps/deci2.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2_dcmp.o -MD -MP -MF ".deps/deci2_dcmp.Tpo" -c -o deci2_dcmp.o deci2_dcmp.c; \
	then mv -f ".deps/deci2_dcmp.Tpo" ".deps/deci2_dcmp.Po"; else rm -f ".deps/deci2_dcmp.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2_ttyp.o -MD -MP -MF ".deps/deci2_ttyp.Tpo" -c -o deci2_ttyp.o deci2_ttyp.c; \
	then mv -f ".deps/deci2_ttyp.Tpo" ".deps/deci2_ttyp.Po"; else rm -f ".deps/deci2_ttyp.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2_dbgp.o -MD -MP -MF ".deps/deci2_dbgp.Tpo" -c -o deci2_dbgp.o deci2_dbgp.c; \
	then mv -f ".deps/deci2_dbgp.Tpo" ".deps/deci2_dbgp.Po"; else rm -f ".deps/deci2_dbgp.Tpo"; exit 1; fi
deci2_dbgp.c: In function ‘D2_DBGP’:
deci2_dbgp.c:177: warning: unknown conversion type character ‘I’ in format
deci2_dbgp.c:177: warning: unknown conversion type character ‘I’ in format
deci2_dbgp.c:348: warning: passing argument 1 of ‘InterlockedExchange’ from incompatible pointer type
deci2_dbgp.c:361: warning: passing argument 1 of ‘InterlockedExchange’ from incompatible pointer type
deci2_dbgp.c:380: warning: passing argument 1 of ‘InterlockedExchange’ from incompatible pointer type
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2_netmp.o -MD -MP -MF ".deps/deci2_netmp.Tpo" -c -o deci2_netmp.o deci2_netmp.c; \
	then mv -f ".deps/deci2_netmp.Tpo" ".deps/deci2_netmp.Po"; else rm -f ".deps/deci2_netmp.Tpo"; exit 1; fi
deci2_netmp.c: In function ‘D2_NETMP’:
deci2_netmp.c:68: warning: 'I' flag used with ‘%X’ printf format
deci2_netmp.c:68: warning: format ‘%I64X’ expects type ‘unsigned int’, but argument 3 has type ‘u64’
deci2_netmp.c:68: warning: 'I' flag used with ‘%X’ printf format
deci2_netmp.c:68: warning: format ‘%I64X’ expects type ‘unsigned int’, but argument 4 has type ‘u64’
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT deci2_iloadp.o -MD -MP -MF ".deps/deci2_iloadp.Tpo" -c -o deci2_iloadp.o deci2_iloadp.c; \
	then mv -f ".deps/deci2_iloadp.Tpo" ".deps/deci2_iloadp.Po"; else rm -f ".deps/deci2_iloadp.Tpo"; exit 1; fi
rm -f libRDebug.a
ar cru libRDebug.a deci2.o deci2_dcmp.o deci2_ttyp.o deci2_dbgp.o deci2_netmp.o deci2_iloadp.o 
ranlib libRDebug.a
make[2]: Entering directory `/home/urd/pcsx2/pcsx2/RDebug'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/urd/pcsx2/pcsx2/RDebug'
make[1]: Leaving directory `/home/urd/pcsx2/pcsx2/RDebug'
Making install in tinyxml
make[1]: Entering directory `/home/urd/pcsx2/pcsx2/tinyxml'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT tinystr.o -MD -MP -MF ".deps/tinystr.Tpo" -c -o tinystr.o tinystr.cpp; \
	then mv -f ".deps/tinystr.Tpo" ".deps/tinystr.Po"; else rm -f ".deps/tinystr.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT tinyxml.o -MD -MP -MF ".deps/tinyxml.Tpo" -c -o tinyxml.o tinyxml.cpp; \
	then mv -f ".deps/tinyxml.Tpo" ".deps/tinyxml.Po"; else rm -f ".deps/tinyxml.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT tinyxmlerror.o -MD -MP -MF ".deps/tinyxmlerror.Tpo" -c -o tinyxmlerror.o tinyxmlerror.cpp; \
	then mv -f ".deps/tinyxmlerror.Tpo" ".deps/tinyxmlerror.Po"; else rm -f ".deps/tinyxmlerror.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT tinyxmlparser.o -MD -MP -MF ".deps/tinyxmlparser.Tpo" -c -o tinyxmlparser.o tinyxmlparser.cpp; \
	then mv -f ".deps/tinyxmlparser.Tpo" ".deps/tinyxmlparser.Po"; else rm -f ".deps/tinyxmlparser.Tpo"; exit 1; fi
rm -f libtinyxml.a
ar cru libtinyxml.a tinystr.o tinyxml.o tinyxmlerror.o tinyxmlparser.o 
ranlib libtinyxml.a
make[2]: Entering directory `/home/urd/pcsx2/pcsx2/tinyxml'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/urd/pcsx2/pcsx2/tinyxml'
make[1]: Leaving directory `/home/urd/pcsx2/pcsx2/tinyxml'
Making install in Linux
make[1]: Entering directory `/home/urd/pcsx2/pcsx2/Linux'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT Config.o -MD -MP -MF ".deps/Config.Tpo" -c -o Config.o Config.c; \
	then mv -f ".deps/Config.Tpo" ".deps/Config.Po"; else rm -f ".deps/Config.Tpo"; exit 1; fi
Config.c: In function ‘LoadConfig’:
Config.c:65: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT interface.o -MD -MP -MF ".deps/interface.Tpo" -c -o interface.o interface.c; \
	then mv -f ".deps/interface.Tpo" ".deps/interface.Po"; else rm -f ".deps/interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT GtkGui.o -MD -MP -MF ".deps/GtkGui.Tpo" -c -o GtkGui.o GtkGui.c; \
	then mv -f ".deps/GtkGui.Tpo" ".deps/GtkGui.Po"; else rm -f ".deps/GtkGui.Tpo"; exit 1; fi
GtkGui.c: In function ‘OnConf_Gs’:
GtkGui.c:499: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:500: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:503: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Pads’:
GtkGui.c:509: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:510: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:514: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Spu2’:
GtkGui.c:520: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:521: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:525: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Cdvd’:
GtkGui.c:530: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:531: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:535: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Dev9’:
GtkGui.c:540: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:541: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:545: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Usb’:
GtkGui.c:550: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:551: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:555: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConf_Fw’:
GtkGui.c:560: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:561: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:565: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_GsConf’:
GtkGui.c:768: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:768: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:768: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_GsAbout’:
GtkGui.c:776: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:776: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:776: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Pad1Conf’:
GtkGui.c:780: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:780: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:780: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Pad1About’:
GtkGui.c:788: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:788: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:788: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Pad2Conf’:
GtkGui.c:792: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:792: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:792: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Pad2About’:
GtkGui.c:800: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:800: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:800: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Spu2Conf’:
GtkGui.c:804: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:804: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:804: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Spu2About’:
GtkGui.c:812: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:812: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:812: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_CdvdConf’:
GtkGui.c:816: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:816: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:816: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_CdvdAbout’:
GtkGui.c:824: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:824: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:824: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Dev9Conf’:
GtkGui.c:828: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:828: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:828: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_Dev9About’:
GtkGui.c:836: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:836: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:836: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_UsbConf’:
GtkGui.c:840: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:840: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:840: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_UsbAbout’:
GtkGui.c:848: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:848: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:848: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_FWConf’:
GtkGui.c:852: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:852: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:852: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘OnConfConf_FWAbout’:
GtkGui.c:860: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
GtkGui.c:860: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c:860: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
GtkGui.c: In function ‘UpdateDebugger’:
GtkGui.c:997: warning: format ‘%8.8lX’ expects type ‘long unsigned int’, but argument 3 has type ‘u32’
GtkGui.c: In function ‘OnSetPC_Ok’:
GtkGui.c:1022: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c: In function ‘OnSetBPA_Ok’:
GtkGui.c:1050: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c: In function ‘OnSetBPC_Ok’:
GtkGui.c:1078: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c: In function ‘OnDumpC_Ok’:
GtkGui.c:1112: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c:1114: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c:1127: warning: format ‘%8.8lX’ expects type ‘long unsigned int’, but argument 3 has type ‘u32’
GtkGui.c: In function ‘OnDumpR_Ok’:
GtkGui.c:1163: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c:1165: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘u32 *’
GtkGui.c:1182: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
GtkGui.c: In function ‘FindPlugins’:
GtkGui.c:1498: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1498: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1498: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1510: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1510: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1510: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1512: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1512: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1512: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1518: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1518: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1518: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1524: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1524: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1524: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1530: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1530: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1530: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1536: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1536: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1536: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
GtkGui.c:1542: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GtkGui.c:1542: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘u32’
GtkGui.c:1542: warning: format ‘%ld’ expects type ‘long int’, but argument 6 has type ‘u32’
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT LnxMain.o -MD -MP -MF ".deps/LnxMain.Tpo" -c -o LnxMain.o LnxMain.c; \
	then mv -f ".deps/LnxMain.Tpo" ".deps/LnxMain.Po"; else rm -f ".deps/LnxMain.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.4\" -DPACKAGE_STRING=\"pcsx2\ 0.9.4\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.4\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./../  -O3 -fomit-frame-pointer   -O3 -fomit-frame-pointer  -MT support.o -MD -MP -MF ".deps/support.Tpo" -c -o support.o support.c; \
	then mv -f ".deps/support.Tpo" ".deps/support.Po"; else rm -f ".deps/support.Tpo"; exit 1; fi
gcc  -O3 -fomit-frame-pointer    -o pcsx2  Config.o interface.o GtkGui.o LnxMain.o support.o ../libpcsx2.a ../IPU/libIPU.a ../IPU/mpeg2lib/libmpeg2IPU.a ../RDebug/libRDebug.a ../tinyxml/libtinyxml.a ../x86/libx86recomp.a ../x86/ix86/libix86.a ../DebugTools/libDebugTools.a -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lstdc++ -lz
make[2]: Entering directory `/home/urd/pcsx2/pcsx2/Linux'
test -z "/home/urd/pcsx2/bin" || mkdir -p -- "/home/urd/pcsx2/bin"
  /usr/bin/install -c 'pcsx2' '/home/urd/pcsx2/bin/pcsx2'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/urd/pcsx2/pcsx2/Linux'
make[1]: Leaving directory `/home/urd/pcsx2/pcsx2/Linux'

```

this was the exit

---

### Post by Grishka on 2009-04-03
> **urd said:**
> ey man thanks i alredy tryit, but i don't know if is ok ... 
<SNIP>

this was the exit

looks OK now, there were no errors, it seems. do 'sudo make install' now, and it should work.

---

### Post by urd on 2009-04-03
> **Grishka said:**
> looks OK now, there were no errors, it seems. do 'sudo make install' now, and it should work.

sorry for the noob question, but where i do that or who i do that??

---

### Post by Grishka on 2009-04-03
> **urd said:**
> sorry for the noob question, but where i do that or who i do that??

just type it at the command line. but maybe you don't have to. try navigating to your pcsx2 directory, there should be an executable you just built. simply double click it, and it should run, hopefully.

---

### Post by rober-mpp on 2009-04-17
Hi guys, i'm trying to compile it on jaunty beta and it's throwing me this output after compiling the plugins.

Does anybody have an idea of what can it be ?

Thanks..


---------------
Building Pcsx2
---------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build... yes
checking force sse3 instructions... sse3
checking force sse4 instructions... sse4
checking gtk+... checking for pkg-config... pkg-config
checking for main in -lstdc++... yes
checking for main in -lz... yes
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
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating DebugTools/Makefile
config.status: creating Linux/Makefile
config.status: creating IPU/Makefile
config.status: creating IPU/mpeg2lib/Makefile
config.status: creating RDebug/Makefile
config.status: creating tinyxml/Makefile
config.status: creating x86/Makefile
config.status: creating x86/ix86/Makefile
config.status: creating ../3rdparty/zlib/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  Debug build?	       no
  Dev build?	           yes
  Force sse3?	           yes
 nls support?   yes
 local plugin inis? no
 custom cflags? no
 memcpy_fast? 
Making clean in Linux
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/Linux'
test -z "pcsx2" || rm -f pcsx2
rm -f *.o
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/Linux'
Making clean in tinyxml
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/tinyxml'
test -z "libtinyxml.a" || rm -f libtinyxml.a
rm -f *.o
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/tinyxml'
Making clean in RDebug
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/RDebug'
test -z "libRDebug.a" || rm -f libRDebug.a
rm -f *.o
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/RDebug'
Making clean in IPU
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU'
Making clean in mpeg2lib
make[2]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU/mpeg2lib'
test -z "libmpeg2IPU.a" || rm -f libmpeg2IPU.a
rm -f *.o
make[2]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU/mpeg2lib'
Making clean in .
make[2]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU'
test -z "libIPU.a" || rm -f libIPU.a
rm -f *.o
make[2]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU'
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/IPU'
Making clean in DebugTools
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/DebugTools'
test -z "libDebugTools.a" || rm -f libDebugTools.a
rm -f *.o
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/DebugTools'
Making clean in x86
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
Making clean in ix86
make[2]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86/ix86'
test -z "libix86.a" || rm -f libix86.a
rm -f *.o
make[2]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86/ix86'
Making clean in .
make[2]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
test -z "libx86recomp.a" || rm -f libx86recomp.a
rm -f *.o
make[2]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
Making clean in .
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2'
test -z "libpcsx2.a" || rm -f libpcsx2.a
rm -f *.o
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2'
Making install in x86
make[1]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
Making install in ix86
make[2]: Entering directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86/ix86'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.6\" -DPACKAGE_STRING=\"pcsx2\ 0.9.6\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.6\" -DSVN_REV=\"Revision:\ 1002\" -DNDEBUG=1 -DPCSX2_DEVBUILD=1 -DPCSX2_FORCESSE3=1 -DPCSX2_FORCESSE4=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DENABLE_NLS=1 -I. -I. -I./.. -I./../../   -I./../../../common/include -I./../../../3rdparty    -pipe -msse -msse2 -O2 -Wno-format -Wno-unused-parameter -Wno-unused-value -Wunused-variable  -fno-guess-branch-probability -fno-dse -fno-tree-dse  -fpermissive -Xlinker -zmuldefs  -MT ix86.o -MD -MP -MF ".deps/ix86.Tpo" -c -o ix86.o ix86.cpp; \
	then mv -f ".deps/ix86.Tpo" ".deps/ix86.Po"; else rm -f ".deps/ix86.Tpo"; exit 1; fi
In file included from ix86_types.h:628,
                 from ix86_internal.h:21,
                 from ix86.cpp:37:
implement/bittest.h: In static member function &#8216;static void x86Emitter::Internal::Group8Impl<InstType, ImmType>::Emit(void*, const x86Emitter::iRegister<ImmType>&)&#8217;:
implement/bittest.h:62: error: request for member &#8216;Id&#8217; in &#8216;bitbase&#8217;, which is of non-class type &#8216;void*&#8217;
make[2]: *** [ix86.o] Error 1
make[2]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86/ix86'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rober/Desktop/pcsx2-read-only/pcsx2/x86'
make: *** [install-recursive] Error 1
Error with building pcsx2

---

### Post by Mynsc on 2009-04-18
Ok I have compiled it without errors, my problem is where is the pscx2 executable to run it?

---

### Post by hikaricore on 2009-04-18
Did you run:

> make install

?

---

### Post by rober-mpp on 2009-04-18
> Did you run:

Quote:
make install
? 

What do you mean? i'm building pcsx2 running 
```
pcsx2-read-only$ ./build.sh all
```

At the source root there is no make file, so running make install doesn't do anything.

---

### Post by hikaricore on 2009-04-18
hrrmmm no clue then, what does the documentation in the pcsx2 directory say to do next?

there's almost always an install guide.

---

### Post by Mynsc on 2009-04-18
ok the installation instructions say:

Linux Users
-----------

Make sure you have these packages:
gtk2
opengl
libbz2
libjpeg
glew-dev
libxxf86vm-dev
x11proto-xf86vidmode
automake and autoconf (verion >= 1.9)
Nvidia Cg-Toolkit ([http://developer.nvidia.com/object/cg_toolkit.html](http://developer.nvidia.com/object/cg_toolkit.html))
libasound-dev
joystick

When first building, the Pcsx2 programs need to configure the Makefiles for your specific OS. type:

# sh build.sh all

The program and all plugins will be installed in the pcsx2 bin dir. After that, just launch pcsx2 (make sure you have a PS2 bios dump in the bios directory).

To rebuild any changes to the source code type:
# sh build.sh install

Typeing sh build.sh without the install will just build the programs without copying them to the bin dirctory (bin/plugins for all plugins).

To clean all object files type:
# sh build.sh clean

If there is a plugin that is giving you errors and you want to skip it, modify the corresponding build.sh to skip it (otherwise execution of the script will stop until the error is resolved).

Special Options (modify PCSX2OPTIONS in build.sh)

--enable-debug {Build with symbols and no optimizations}
--enable-devbuild {Build with extra tests}
--disable-recbuild {Disables all architecture dependent recompilation code}
--enable-sse2 {Enables x86 SSE2 extensions}
--enable-sse3 {Force enables x86 SSE3 extensions}

For plugin authors: Your Makefile should support the 'install' option.

When debugging, make sure to add

handle SIGSEGV noprint ignore pass

to .gdbinit
________

Now I did sh build.sh all as was mentioned in [http://ubuntuforums.org/showthread.php?t=399165&highlight=pcsx2]("http://ubuntuforums.org/showthread.php?t=399165&highlight=pcsx2")

I just can't find the executable or command to run pcsx2.

---

### Post by rober-mpp on 2009-04-18
It's not in the bin folder? Sounds like it should be there, at least for me.

In my case, i can't finish the compiling process. It fails after compiling the plugins when running "sh build.sh all".

I've also tried with the --enable-sse3 option, but it didn't work either.

Thanks

---

### Post by zero777zero on 2009-04-18
a jaunty deb on getdeb.net would do a lot of us non-programmers good

---

### Post by hikaricore on 2009-04-18
Not sure what the latest version of pcsx2 is but getdeb has a hardy package for 0.9.4: [http://www.getdeb.net/app/PCSX2](http://www.getdeb.net/app/PCSX2)

It should still be fine even on newer releases. :p

---

### Post by octo_flush on 2009-04-18
I am having the same problem as rober-mpp:

```
implement/bittest.h:62: error: request for member &#8216;Id&#8217; in &#8216;bitbase&#8217;, which is of non-class type &#8216;void*&#8217;
```

It is complaining about the id access here in bittest.h:
```
static __emitinline void Emit( void* bitbase, const iRegister<ImmType>& bitoffset )
	{
		prefix16();
		iWrite<u8>( 0x0f );
		iWrite<u8>( 0xa3 | (InstType << 2) );
		iWriteDisp( bitoffset.Id, bitbase.Id );
	}
```

If I comment out the code mentioned above from bittest.h, The compilation proceeds until I get this error:

[CODE]In file included from Common.h:35,
                 from RecoverySystem.cpp:21:
SaveState.h:220:7: warning: no newline at end of file
In file included from RecoverySystem.cpp:22:
HostGui.h:100:3: warning: no newline at end of file
RecoverySystem.cpp:38: error: &#8216;__COUNTER__&#8217; was not declared in this scope
RecoverySystem.cpp:38: error: template argument 1 is invalid
RecoverySystem.cpp:51: error: &#8216;__COUNTER__&#8217; was not declared in this scope
RecoverySystem.cpp:51: error: template argument 1 is invalid
RecoverySystem.cpp:62: error: &#8216;__COUNTER__&#8217; was not declared in this scope
RecoverySystem.cpp:62: error: template argument 1 is invalid
[CODE]

I added the following to the beginning of RecoverySystem.cpp:
[CODE]
#ifndef __COUNTER__
	#define __COUNTER__ 1
#else
	#define __COUNTER__ __COUNTER__+1
#endif
[CODE]

and compilation proceeds until:

[CODE]
Mpeg.cpp: In function &#8216;void waitForSCD()&#8217;:
Mpeg.cpp:979: error: &#8216;__builtin_bswap32&#8217; was not declared in this scope
[CODE]

---

### Post by eponymous on 2009-04-20
Man I have tried everything I can find searching for this, but nothing works.

I can configure everything OK, but then when I go to run pcsx2 I get the following error
```
ZeroPAD: failed to load ini /home/phil/pcsx2/bin/inis/zeropad.ini
*** buffer overflow detected ***: pcsx2 terminated
```

Any ideas? I've tried configuring all the gamepad buttons, selecting "no gamepad" to use the keyboard, tried configuring every plugin and configuring no plugins. Always the same error! I get the feeling it's not actually related to the zeropad plugin but it's some other problem, but i'm pretty much a noob so any help would be much appreciated.

---

### Post by zero777zero on 2009-04-25
i tried out the new linux binary (the older .deb packages dont work at all for me) and i got a weird video error, one plugin will crash PCSX2 for me and another one will give a messed up screen

---

### Post by Devi 710 on 2009-04-29
> **zero777zero said:**
> a jaunty deb on getdeb.net would do a lot of us non-programmers good

I second that! I would love for the new version to be put into a .deb file for 9.04. I could never get it going on my own.:(

---

### Post by rober-mpp on 2009-04-29
> i tried out the new linux binary (the older .deb packages dont work at all for me) and i got a weird video error, one plugin will crash PCSX2 for me and another one will give a messed up screen

What do you mean with "new linux binary" ? 

Where did you get it ?


thanks

---

### Post by Nevon on 2009-04-30
I don't know if it's the latest version or not, but pcsx-df is in the repositories.

---

### Post by rober-mpp on 2009-04-30
that's the binary for the ps1 emulator, not for the ps2 emulator.

---

### Post by Nevon on 2009-05-01
> **rober-mpp said:**
> that's the binary for the ps1 emulator, not for the ps2 emulator.

Oh I'm sorry. I thought this was about PCSX, not PCSX2. :P

---

### Post by jimmah6786 on 2009-06-01
Not sure why I cannot build the ZeroPAD part. Perhaps someone with there infinite wisdom may assist.

Thanks all
-Jim

```

Building ZeroPAD
----------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for a x86-64 CPU... yes
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for SDL_Init in -lSDL... no
checking gtk2+... checking for pkg-config... pkg-config
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
checking for main in -lstdc++... yes
checking for main in -ldl... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
Configuration:
  Debug build?	       no
  x86-64 build?	       yes
test -z "libZeroPAD.a" || rm -f libZeroPAD.a
test -z "libZeroPAD.so.0.2.0" || rm -f libZeroPAD.so.0.2.0
rm -f *.o
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -D__x86_64__=1 -I.    -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -O2 -fomit-frame-pointer   -MT libZeroPAD_a-zeropad.o -MD -MP -MF .deps/libZeroPAD_a-zeropad.Tpo -c -o libZeroPAD_a-zeropad.o `test -f 'zeropad.cpp' || echo './'`zeropad.cpp
zeropad.cpp:34: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘s32 PADinit(u32)’:
zeropad.cpp:168: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp:177: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result
zeropad.cpp: In function ‘u8 PADstartPoll(int)’:
zeropad.cpp:251: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 _PADpoll(u8)’:
zeropad.cpp:265: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp:400: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 PADpoll(u8)’:
zeropad.cpp:470: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroPAD_a-zeropad.Tpo .deps/libZeroPAD_a-zeropad.Po
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -D__x86_64__=1 -I.    -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -O2 -fomit-frame-pointer   -MT libZeroPAD_a-linux.o -MD -MP -MF .deps/libZeroPAD_a-linux.Tpo -c -o libZeroPAD_a-linux.o `test -f 'Linux/linux.cpp' || echo './'`Linux/linux.cpp
Linux/linux.cpp:25:21: error: SDL/SDL.h: No such file or directory
Linux/linux.cpp:71: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:71: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:74: error: expected `;' before ‘private’
Linux/linux.cpp:85: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:85: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp: In function ‘void LoadConfig()’:
Linux/linux.cpp:163: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp:166: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp:167: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Linux/linux.cpp: In function ‘void PADupdate(int)’:
Linux/linux.cpp:319: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:328: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:328: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:340: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:340: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp:344: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:353: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:362: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:371: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:388: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:388: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp: In function ‘void UpdateConf(int)’:
Linux/linux.cpp:437: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp:441: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp:445: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
Linux/linux.cpp: In function ‘void OnConf_Key(GtkButton*, void*)’:
Linux/linux.cpp:499: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:525: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:525: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:542: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:542: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp:546: error: ‘abs’ was not declared in this scope
Linux/linux.cpp:553: error: ‘abs’ was not declared in this scope
Linux/linux.cpp: In static member function ‘static void JoystickInfo::EnumerateJoysticks(std::vector<JoystickInfo*, std::allocator<JoystickInfo*> >&)’:
Linux/linux.cpp:717: error: ‘SDL_INIT_JOYSTICK’ was not declared in this scope
Linux/linux.cpp:717: error: ‘SDL_Init’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_QUERY’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_JoystickEventState’ was not declared in this scope
Linux/linux.cpp:726: error: ‘SDL_NumJoysticks’ was not declared in this scope
Linux/linux.cpp: In constructor ‘JoystickInfo::JoystickInfo()’:
Linux/linux.cpp:753: error: ‘joy’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::Destroy()’:
Linux/linux.cpp:764: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:765: error: ‘SDL_JoystickOpened’ was not declared in this scope
Linux/linux.cpp:766: error: ‘SDL_JoystickClose’ was not declared in this scope
Linux/linux.cpp: In member function ‘bool JoystickInfo::Init(int, bool)’:
Linux/linux.cpp:778: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:778: error: ‘SDL_JoystickOpen’ was not declared in this scope
Linux/linux.cpp:784: error: ‘SDL_JoystickNumAxes’ was not declared in this scope
Linux/linux.cpp:785: error: ‘SDL_JoystickNumButtons’ was not declared in this scope
Linux/linux.cpp:786: error: ‘SDL_JoystickNumHats’ was not declared in this scope
Linux/linux.cpp:787: error: ‘SDL_JoystickName’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::SaveState()’:
Linux/linux.cpp:821: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:821: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:823: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:823: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
make: *** [libZeroPAD_a-linux.o] Error 1
Error with building plugins


```

---

### Post by josko88 on 2009-08-12
> **jimmah6786 said:**
> Not sure why I cannot build the ZeroPAD part. Perhaps someone with there infinite wisdom may assist.

Thanks all
-Jim

```

Building ZeroPAD
----------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for a x86-64 CPU... yes
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for SDL_Init in -lSDL... no
checking gtk2+... checking for pkg-config... pkg-config
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
checking for main in -lstdc++... yes
checking for main in -ldl... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
Configuration:
  Debug build?	       no
  x86-64 build?	       yes
test -z "libZeroPAD.a" || rm -f libZeroPAD.a
test -z "libZeroPAD.so.0.2.0" || rm -f libZeroPAD.so.0.2.0
rm -f *.o
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -D__x86_64__=1 -I.    -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -O2 -fomit-frame-pointer   -MT libZeroPAD_a-zeropad.o -MD -MP -MF .deps/libZeroPAD_a-zeropad.Tpo -c -o libZeroPAD_a-zeropad.o `test -f 'zeropad.cpp' || echo './'`zeropad.cpp
zeropad.cpp:34: warning: deprecated conversion from string constant to &#8216;char*&#8217;
zeropad.cpp: In function &#8216;s32 PADinit(u32)&#8217;:
zeropad.cpp:168: warning: deprecated conversion from string constant to &#8216;char*&#8217;
zeropad.cpp:177: warning: ignoring return value of &#8216;char* getcwd(char*, size_t)&#8217;, declared with attribute warn_unused_result
zeropad.cpp: In function &#8216;u8 PADstartPoll(int)&#8217;:
zeropad.cpp:251: warning: deprecated conversion from string constant to &#8216;char*&#8217;
zeropad.cpp: In function &#8216;u8 _PADpoll(u8)&#8217;:
zeropad.cpp:265: warning: deprecated conversion from string constant to &#8216;char*&#8217;
zeropad.cpp:400: warning: deprecated conversion from string constant to &#8216;char*&#8217;
zeropad.cpp: In function &#8216;u8 PADpoll(u8)&#8217;:
zeropad.cpp:470: warning: deprecated conversion from string constant to &#8216;char*&#8217;
mv -f .deps/libZeroPAD_a-zeropad.Tpo .deps/libZeroPAD_a-zeropad.Po
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -D__x86_64__=1 -I.    -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -O2 -fomit-frame-pointer   -MT libZeroPAD_a-linux.o -MD -MP -MF .deps/libZeroPAD_a-linux.Tpo -c -o libZeroPAD_a-linux.o `test -f 'Linux/linux.cpp' || echo './'`Linux/linux.cpp
Linux/linux.cpp:25:21: error: SDL/SDL.h: No such file or directory
Linux/linux.cpp:71: error: ISO C++ forbids declaration of &#8216;SDL_Joystick&#8217; with no type
Linux/linux.cpp:71: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Linux/linux.cpp:74: error: expected `;' before &#8216;private&#8217;
Linux/linux.cpp:85: error: ISO C++ forbids declaration of &#8216;SDL_Joystick&#8217; with no type
Linux/linux.cpp:85: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Linux/linux.cpp: In function &#8216;void LoadConfig()&#8217;:
Linux/linux.cpp:163: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Linux/linux.cpp:166: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Linux/linux.cpp:167: warning: ignoring return value of &#8216;int fscanf(FILE*, const char*, ...)&#8217;, declared with attribute warn_unused_result
Linux/linux.cpp: In function &#8216;void PADupdate(int)&#8217;:
Linux/linux.cpp:319: error: &#8216;SDL_JoystickUpdate&#8217; was not declared in this scope
Linux/linux.cpp:328: error: &#8216;class JoystickInfo&#8217; has no member named &#8216;GetJoy&#8217;
Linux/linux.cpp:328: error: &#8216;SDL_JoystickGetButton&#8217; was not declared in this scope
Linux/linux.cpp:340: error: &#8216;class JoystickInfo&#8217; has no member named &#8216;GetJoy&#8217;
Linux/linux.cpp:340: error: &#8216;SDL_JoystickGetAxis&#8217; was not declared in this scope
Linux/linux.cpp:344: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp:353: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp:362: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp:371: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp:388: error: &#8216;class JoystickInfo&#8217; has no member named &#8216;GetJoy&#8217;
Linux/linux.cpp:388: error: &#8216;SDL_JoystickGetAxis&#8217; was not declared in this scope
Linux/linux.cpp: In function &#8216;void UpdateConf(int)&#8217;:
Linux/linux.cpp:437: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
Linux/linux.cpp:441: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
Linux/linux.cpp:445: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
Linux/linux.cpp: In function &#8216;void OnConf_Key(GtkButton*, void*)&#8217;:
Linux/linux.cpp:499: error: &#8216;SDL_JoystickUpdate&#8217; was not declared in this scope
Linux/linux.cpp:525: error: &#8216;class JoystickInfo&#8217; has no member named &#8216;GetJoy&#8217;
Linux/linux.cpp:525: error: &#8216;SDL_JoystickGetButton&#8217; was not declared in this scope
Linux/linux.cpp:542: error: &#8216;class JoystickInfo&#8217; has no member named &#8216;GetJoy&#8217;
Linux/linux.cpp:542: error: &#8216;SDL_JoystickGetAxis&#8217; was not declared in this scope
Linux/linux.cpp:546: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp:553: error: &#8216;abs&#8217; was not declared in this scope
Linux/linux.cpp: In static member function &#8216;static void JoystickInfo::EnumerateJoysticks(std::vector<JoystickInfo*, std::allocator<JoystickInfo*> >&)&#8217;:
Linux/linux.cpp:717: error: &#8216;SDL_INIT_JOYSTICK&#8217; was not declared in this scope
Linux/linux.cpp:717: error: &#8216;SDL_Init&#8217; was not declared in this scope
Linux/linux.cpp:719: error: &#8216;SDL_QUERY&#8217; was not declared in this scope
Linux/linux.cpp:719: error: &#8216;SDL_JoystickEventState&#8217; was not declared in this scope
Linux/linux.cpp:726: error: &#8216;SDL_NumJoysticks&#8217; was not declared in this scope
Linux/linux.cpp: In constructor &#8216;JoystickInfo::JoystickInfo()&#8217;:
Linux/linux.cpp:753: error: &#8216;joy&#8217; was not declared in this scope
Linux/linux.cpp: In member function &#8216;void JoystickInfo::Destroy()&#8217;:
Linux/linux.cpp:764: error: &#8216;joy&#8217; was not declared in this scope
Linux/linux.cpp:765: error: &#8216;SDL_JoystickOpened&#8217; was not declared in this scope
Linux/linux.cpp:766: error: &#8216;SDL_JoystickClose&#8217; was not declared in this scope
Linux/linux.cpp: In member function &#8216;bool JoystickInfo::Init(int, bool)&#8217;:
Linux/linux.cpp:778: error: &#8216;joy&#8217; was not declared in this scope
Linux/linux.cpp:778: error: &#8216;SDL_JoystickOpen&#8217; was not declared in this scope
Linux/linux.cpp:784: error: &#8216;SDL_JoystickNumAxes&#8217; was not declared in this scope
Linux/linux.cpp:785: error: &#8216;SDL_JoystickNumButtons&#8217; was not declared in this scope
Linux/linux.cpp:786: error: &#8216;SDL_JoystickNumHats&#8217; was not declared in this scope
Linux/linux.cpp:787: error: &#8216;SDL_JoystickName&#8217; was not declared in this scope
Linux/linux.cpp: In member function &#8216;void JoystickInfo::SaveState()&#8217;:
Linux/linux.cpp:821: error: &#8216;joy&#8217; was not declared in this scope
Linux/linux.cpp:821: error: &#8216;SDL_JoystickGetButton&#8217; was not declared in this scope
Linux/linux.cpp:823: error: &#8216;joy&#8217; was not declared in this scope
Linux/linux.cpp:823: error: &#8216;SDL_JoystickGetAxis&#8217; was not declared in this scope
make: *** [libZeroPAD_a-linux.o] Error 1
Error with building plugins


```

apt-get install libsdl1.2-dev or possibly libsdl-dev

I get this problem trying anything newer then 0.9.6. including that version:

```
gcc  -O3 -fomit-frame-pointer -fPIC -Wall  -Wno-unused-value -m32  -shared -Wl,-soname,@libCDVDnull_SONAME@  -o libCDVDnull.so.0.8.0  libCDVDnull_a-CDVD.o libCDVDnull_a-Config.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld returned 1 exit status
make: *** [libCDVDnull.so.0.8.0] Error 1
Error with building plugins

```

Also used some random revisions from SVN :-/

---

### Post by sarareid on 2009-09-02
Yes I have heard about this.
I have also heard that I can install ps2 on fedora with the help of this new upgrade epcx.
Does anyone is there who have actually installed this and use this on linux?Does it supports all the games which can be played on windows?
what other games I can play on it with the help of thi ecpx ?

---

### Post by PhoeniX1992 on 2009-10-19
I've tried almost anything, but I can't get it to work, this is the error I keep receiving after trying to build

```
phoenix@PhoeniX:~/pcsx2$ sudo sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
Making clean in .
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl' wordt binnengegaan
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl' wordt verlaten
Making install in Linux
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt binnengegaan
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In bestand ingevoegd vanuit Conf.cpp:25:
../GS.h:41:21: fout: GL/glew.h: Bestand of map bestaat niet
Conf.cpp: In function &#8216;void LoadConfig()&#8217;:
Conf.cpp:66: let op: de returnwaarde van &#8216;int fscanf(FILE*, const char*, ...)&#8217;, gedeclareerd met het &#8216;warn_unused_result&#8217; atribuut, wordt genegeerd
Conf.cpp:67: let op: de returnwaarde van &#8216;int fscanf(FILE*, const char*, ...)&#8217;, gedeclareerd met het &#8216;warn_unused_result&#8217; atribuut, wordt genegeerd
Conf.cpp:68: let op: de returnwaarde van &#8216;int fscanf(FILE*, const char*, ...)&#8217;, gedeclareerd met het &#8216;warn_unused_result&#8217; atribuut, wordt genegeerd
Conf.cpp:69: let op: de returnwaarde van &#8216;int fscanf(FILE*, const char*, ...)&#8217;, gedeclareerd met het &#8216;warn_unused_result&#8217; atribuut, wordt genegeerd
Conf.cpp:70: let op: de returnwaarde van &#8216;int fscanf(FILE*, const char*, ...)&#8217;, gedeclareerd met het &#8216;warn_unused_result&#8217; atribuut, wordt genegeerd
make[1]: *** [libZeroGSLinux_a-Conf.o] Fout 1
make[1]: Map '/home/phoenix/pcsx2/plugins/gs/zerogs/opengl/Linux' wordt verlaten
make: *** [install-recursive] Fout 1
Error with building plugins

```

PCSX (PS1 emulator) works fine for me tough...

---

### Post by gimmickless on 2009-11-27
I've also got problems with compiling.  I've scanned through the entire thread, pasting in commands and most all the quick fixes.  Only thing I've done differently is that I've got libsdl1.2debian-all installed instead of -alsa.

Here's the results of build:

```
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... yes
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       yes
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF ".deps/libZeroGSLinux_a-interface.Tpo" -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c; \
	then mv -f ".deps/libZeroGSLinux_a-interface.Tpo" ".deps/libZeroGSLinux_a-interface.Po"; else rm -f ".deps/libZeroGSLinux_a-interface.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF ".deps/libZeroGSLinux_a-Linux.Tpo" -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Linux.Tpo" ".deps/libZeroGSLinux_a-Linux.Po"; else rm -f ".deps/libZeroGSLinux_a-Linux.Tpo"; exit 1; fi
Linux.cpp: In function ‘void GSconfigure()’:
Linux.cpp:240: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:243: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:246: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:249: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:252: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:255: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:258: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:261: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:264: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:267: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:270: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:273: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:276: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:279: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:282: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:285: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:288: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:291: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:294: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:297: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:300: warning: deprecated conversion from string constant to ‘char*’
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF ".deps/libZeroGSLinux_a-support.Tpo" -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c; \
	then mv -f ".deps/libZeroGSLinux_a-support.Tpo" ".deps/libZeroGSLinux_a-support.Po"; else rm -f ".deps/libZeroGSLinux_a-support.Tpo"; exit 1; fi
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF ".deps/libZeroGSogl_a-GSmain.Tpo" -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp; \
	then mv -f ".deps/libZeroGSogl_a-GSmain.Tpo" ".deps/libZeroGSogl_a-GSmain.Po"; else rm -f ".deps/libZeroGSogl_a-GSmain.Tpo"; exit 1; fi
In file included from GSmain.cpp:39:
zerogs.h:41:19: error: Cg/cg.h: No such file or directory
zerogs.h:42:21: error: Cg/cgGL.h: No such file or directory
In file included from GSmain.cpp:39:
zerogs.h:124: error: ‘CGprogram’ does not name a type
zerogs.h:132: error: ‘CGprogram’ does not name a type
zerogs.h:133: error: ‘CGparameter’ does not name a type
zerogs.h:134: error: ‘CGparameter’ does not name a type
zerogs.h:135: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘FRAGMENTSHADER::FRAGMENTSHADER()’:
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘prog’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sMemory’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sFinal’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDX’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitwiseANDY’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sInterlace’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sCLUT’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sOneColor’
zerogs.h:128: error: class ‘FRAGMENTSHADER’ does not have any field named ‘sBitBltZ’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha2’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexOffset’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexDims’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexBlock’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fClampExts’
zerogs.h:129: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexWrapMode’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fRealTexDims’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTestBlack’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fPageOffset’
zerogs.h:130: error: class ‘FRAGMENTSHADER’ does not have any field named ‘fTexAlpha’
zerogs.h: At global scope:
zerogs.h:145: error: ‘CGprogram’ does not name a type
zerogs.h:146: error: ‘CGparameter’ does not name a type
zerogs.h: In constructor ‘VERTEXSHADER::VERTEXSHADER()’:
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘prog’
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltPos’
zerogs.h:144: error: class ‘VERTEXSHADER’ does not have any field named ‘sBitBltTex’
zerogs.h: At global scope:
zerogs.h:182: error: ‘CGparameter’ does not name a type
In file included from GSmain.cpp:41:
ZeroGSShaders/zerogsshaders.h:27: error: ‘CGcontext’ does not name a type
ZeroGSShaders/zerogsshaders.h:29: error: ‘CGprogram’ does not name a type
GSmain.cpp:74: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSsetGameCRC(int, int)’:
GSmain.cpp:169: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘s32 GSinit()’:
GSmain.cpp:273: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:277: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:290: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:282: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result
GSmain.cpp: In function ‘s32 GSopen(void*, char*, int)’:
GSmain.cpp:600: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:614: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:619: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:634: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSmakeSnapshot(char*)’:
GSmain.cpp:728: warning: format ‘%03ld’ expects type ‘long int’, but argument 4 has type ‘u32’
GSmain.cpp:744: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
GSmain.cpp: In function ‘void GSvsync(int)’:
GSmain.cpp:765: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void _GSgifTransfer(pathInfo*, u32*, u32)’:
GSmain.cpp:978: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:992: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:1096: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSgifTransfer1(u32*, u32)’:
GSmain.cpp:1162: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘s32 GSfreeze(int, freezeData*)’:
GSmain.cpp:1209: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void DVProfEnd(u32)’:
GSmain.cpp:1341: warning: deprecated conversion from string constant to ‘char*’
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/gimmickless/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins
```

Y'all are pretty good with support normally.  I'd like to know what else I need to do to get this up and running.

---

### Post by Beguiler on 2009-12-01
Could you elaborate on the dependency you're talking about? I'm having the same issue, and I am no where near an expert on Linux.

---

### Post by Zenitur on 2010-02-19
> **octo_flush said:**
> I added the following to the beginning of RecoverySystem.cpp:
[CODE]
#ifndef __COUNTER__
    #define __COUNTER__ 1
#else
    #define __COUNTER__ __COUNTER__+1
#endif
[CODE]

and compilation proceeds until:

[CODE]
Mpeg.cpp: In function ‘void waitForSCD()’:
Mpeg.cpp:979: error: ‘__builtin_bswap32’ was not declared in this scope
[CODE]
You need remove new mpeg2lib directory and download old version from 426 branch: http://code.google.com/p/pcsx2/source/browse/?r=450#svn/trunk/pcsx2/IPU/mpeg2lib . There is it.
We see this error because __builtin_bswap32 was not realized in GCC 4.2.x. It was realized in GCC 4.3. All other parts of PCSX2 will compile without problems.

---

### Post by Holmen on 2010-04-18
I am unable to compile using the first post. 
Running 64-bit Lucid.

---

### Post by EarthMind on 2010-04-18
Great stuff! I have to try this out :)

---

### Post by sleepee on 2010-04-29
> **Holmen said:**
> I am unable to compile using the first post. 
Running 64-bit Lucid.

try downloading the linux version from here:

[http://pcsx2.net/downloads.php](http://pcsx2.net/downloads.php)

no compiling needed.  just download the tarball, extract, and run the executable.  

the Zeropad controller plugin doesn't pick up my gamepad's left analog stick for me for some reason (seems like that Zeropad plugin is a problem for a lot of people), but the program runs fine from the little bit i've used it...

---

### Post by Hate on 2010-04-29
I hadn't any problem running it, I've tried with my ps2 dvds and everything works good (even if with some minor bug) but is there a way to run iso ? because I can't find in the dvd plugin list the plugin that should manage isos...(I'm kinda tired of switching disks and a couple of my disks have scratches and they're giving me some problems while playing )

---

### Post by aprilie on 2010-05-02
sorry guys but does not work on accer aspire 5570z
I just tried already 
on their website does not say on what hardware works

---

### Post by DartJulius on 2010-06-27
plz.. help... 

> ~/pcsx2/bin$ ./pcsx2

_openfile /home/dartjulius/D/FINAL_FANTASY_X.iso 0
detected blocksize = 2048
isoOpen: /home/dartjulius/D/FINAL_FANTASY_X.iso ok
offset = 0
blockofs = 24
blocksize = 2048
blocks = 2246432
type = 2
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.4
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
[COLOR=Red]Sound device not available![/COLOR]
ZeroGS: Disabling MRT depth writing
[COLOR=Red]Illegal [/COLOR][COLOR=Red]Instruction[/COLOR]tks!

UBUNTU 10.04, 64bits
DUAL CORE 1.6
NVIDIA 7300GS
3GB RAM

---

### Post by xenogia on 2010-06-27
Is there a way to get this running on 64bit Ubuntu.  A work around with 32bit libraries maybe?

---

### Post by Linux4Pedro on 2010-06-30
I did everything as you suggested and i got an error with building plugins. This is the output i got on my terminal:----------------------------------------maybe you can tell me whats wrong. Thanks
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... yes
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?           yes
  Debug build?           no
  Dev build?               no
  SSE2 enabled?           yes
Making clean in Linux
make[1]: Entering directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
    then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -D__x86_64__=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I. -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
    then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/bedrock/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

---

### Post by Perfect Storm on 2010-07-01
May be:
> checking for main in -lGLEW... no

and

> ../GS.h:41:21: error: GL/glew.h: No such file or directory


Try install glew dev package.

---

### Post by Funnnny on 2010-07-01
Anyone success in getting 0.9.7 run on 64bit ?

---

### Post by Sockerdrickan on 2010-07-01
forums stuck

---

### Post by wingnux on 2010-07-07
> **Funnnny said:**
> Anyone success in getting 0.9.7 run on 64bit ?

The pcsx2 devs recommend to run it via a 32bit chroot. I've opted for a 32bit install solely for the purpose of running pcsx2 and I'm really happy with it :D.

---

### Post by d3v1150m471c on 2010-07-17
... what am I doing wrong?
```

d3v11@laptop:~/Downloads/pcsx2-0.9.4$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?           no
  Debug build?           no
  Dev build?               no
  SSE2 enabled?           yes
Making clean in Linux
make[1]: Entering directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl'
Making install in Linux
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
make[1]: Entering directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I.  -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
    then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
callbacks.c:5:21: error: gtk/gtk.h: No such file or directory
In file included from callbacks.c:7:
callbacks.h:5: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
callbacks.h:9: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
callbacks.h:13: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from callbacks.c:8:
interface.h:5: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
interface.h:6: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from callbacks.c:9:
support.h:46: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
support.h:51: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
support.h:59: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
support.h:63: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
support.h:66: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
callbacks.c:13: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
callbacks.c:21: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
callbacks.c:29: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
make[1]: *** [libZeroGSLinux_a-callbacks.o] Error 1
make[1]: Leaving directory `/home/d3v11/Downloads/pcsx2-0.9.4/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins
d3v11@laptop:~/Downloads/pcsx2-0.9.4$ 


```

---

### Post by pi3ch on 2010-10-05
I get in compiled on Ubuntu 10.04 by installing following libs:
 libglew1.5-dev libxxf86vm-dev libasound2-dev libportaudio0 portaudio19-dev joystick libsdl1.2-dev

so her are the steps:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```

```
sudo apt-get install libglu1-mesa-dev 
```

```
sudo apt-get install libglew1.5-dev libxxf86vm-dev libasound2-dev libportaudio0 portaudio19-dev joystick libsdl1.2-dev
```

I could not find two nvidia-cg-toolkit and lib-portaudio-dev that mentioned [here]("http://pcsx2.net/downloads.php?p=publicbeta"). but anyhow I get it compiled and run.

by the end of the day I could not run any game! I get "**Error Opening GS Plugin**"
any idea on how to fix this annoying prompt? :confused:

---

### Post by Perfect Storm on 2010-10-05
sudo apt-get install nvidia-cg-toolkit portaudio19-dev


If they are not there check if your sourcelist is correctly set. It may be the stuff that gives you the errors if they are not enabled into the app.
Do also check the output of the configure script if anything is missing.

---

### Post by Maheriano on 2010-10-05
I haven't checked back on thie progress of this in a while, are we still responsible for dumping our own ROM from the Playstation or has that been simplified? I have 2 Playstation 2, I just don't understand the process.

---

### Post by pi3ch on 2010-10-06
I already got those two nvidia-cg-toolkit portaudio19-dev.
Installed latest version from "http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu" (added to repositories) 
Same error. However, when I choose (libzzogl) I get some bad quality output and slow.

Just give it up for a while see what would be next option for Ps2 on ubuntu

---

### Post by wingnux on 2010-10-07
The latest beta was released at [http://pcsx2.net/](http://pcsx2.net/) and it's really good! =)

---

### Post by ahmed shabayek on 2010-12-02
need help installing the pcsx2 0.9.7 i am running 10.10 64 and ./pcsx2 gives me ./pcsx2: error while loading shared libraries: libwx_baseu-2.8.so.0: cannot open shared object file: No such file or directory so wat should i do

---

### Post by thatguruguy on 2010-12-02
> **ahmed shabayek said:**
> need help installing the pcsx2 0.9.7 i am running 10.10 64 and ./pcsx2 gives me ./pcsx2: error while loading shared libraries: libwx_baseu-2.8.so.0: cannot open shared object file: No such file or directory so wat should i do

My advice would be to install the official pcsx2 repository, which is available [here]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa").  Then you can just install pcsx2 from synaptic.

Scratch that.  I just noticed you're running 64-bit.  Get the following ppa, instead: [https://launchpad.net/~micove/+archive/experimental]("https://launchpad.net/%7Emicove/+archive/experimental"). He includes a 64-bit pcsx2.

---

### Post by ahmed shabayek on 2010-12-03
thnx a lot guru guy that worked i didnt imagine it would be tht simple, i was begining to try the chroot thing thnx again u saved me alot of time:D:D

---

### Post by ahmed shabayek on 2010-12-05
i have a problem when trying to run an iso file it gives this error:

---

### Post by thatguruguy on 2010-12-05
Not every game works.  You can check the compatibility of a particular game by going [here]("http://pcsx2.wikia.com/wiki/Category:Games").

---

### Post by ahmed shabayek on 2010-12-07
i ve tried it on windows it worked on the old pcsx2 0.9.6 and the wiki only mentions very few games ill try some more games/ thnx again for ur help

---

### Post by Mazukambax on 2010-12-31
Ubuntu 10.10 amd64 PCSX2 0.9.7
Graphics Nvidia GeFocrce 6100  512MB 32 bit interpreter
1888 ram
(pxActionEvent) GS plugin failed to open!(thread:MTGS)(thread:EE Core)

what this means? 
should i run it by chroot...?

---

### Post by sephiroth135 on 2011-02-02
> **thatguruguy said:**
> My advice would be to install the official pcsx2 repository, which is available [here]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa").  Then you can just install pcsx2 from synaptic.

Scratch that.  I just noticed you're running 64-bit.  Get the following ppa, instead: [https://launchpad.net/~micove/+archive/experimental]("https://launchpad.net/%7Emicove/+archive/experimental"). He includes a 64-bit pcsx2.

He/she should probably add this one instead:
deb [http://ppa.launchpad.net/micove/console/ubuntu](http://ppa.launchpad.net/micove/console/ubuntu) YOUR_UBUNTU_VERSION_HERE main

Edit: heh apparently I'm still beta testing jaunty and using interpid (should update that).

---

### Post by tigerlily09 on 2011-04-13
[SIZE=2]Hello,[/SIZE]
 
[SIZE=2]I'm trying to get this working but I keep running into issues. I've looked here and at the PCSX2 forums but I'm still stumped. This is my setup:[/SIZE]
 
[SIZE=2]Ubuntu 10.04[/SIZE]
[SIZE=2]AMD Phenom II X3 2.8 GHz[/SIZE]
[SIZE=2]GeForce 9400 GT[/SIZE]
 
[SIZE=2]I was able to compile it cleanly using SVN but but when I start up FFX I get a black screen for a few seconds, then it disappears and takes the PCSX2 window with it.[/SIZE]
 
[SIZE=2]This is the output when I try to run FFX from an ISO. If I try opening the disc it will give me a black window and then hangs, so I'm wondering if I have CDROM issues as well.[/SIZE]
 
>  
[FONT=Courier New][SIZE=2]ZeroGS: creating[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Got Doublebuffered Visual![/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: glX-Version 1.4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Depth 24[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: you have Direct Rendering![/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Disabling MRT depth writing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Creating effects[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Creating extra effects[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: using accurate shaders[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: initialization successful[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Disabling MRT depth writing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Cg error: CG ERROR : Invalid parameter handle.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Cg error: CG ERROR : Invalid parameter handle.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Cg error: CG ERROR : Invalid parameter handle.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Cg error: CG ERROR : Invalid parameter handle.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Cg error: CG ERROR : Invalid parameter handle.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ZeroGS: Failed to create shader 1,0,0,10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Segmentation fault[/SIZE][/FONT]
 
 
[FONT=Courier New]
[FONT=Verdana][SIZE=2]If I turn anti-aliasing on, this is the output:[/SIZE][/FONT]
 
> 
[FONT=Courier New][QUOTE]
[SIZE=2][FONT=Courier New][FONT=Courier New][FONT=Courier New][SIZE=2]ZeroGS: Disabling MRT depth writing[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]ZeroGS: creating[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Got Doublebuffered Visual![/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: glX-Version 1.4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Depth 24[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: you have Direct Rendering![/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Disabling MRT depth writing[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Creating effects[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Creating extra effects[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: using accurate shaders[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: initialization successful[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ZeroGS: Disabling MRT depth writing[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Segmentation fault[/FONT][/SIZE]
[/FONT][/FONT][/SIZE] 
[/FONT]
[FONT=Courier New][FONT=Verdana][SIZE=2]This is the output from when I compiled PCSX2:[/SIZE][/FONT]
 
> 
[FONT=Courier New][FONT=Courier New][SIZE=2]----------------------[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]Building ZeroGS OpenGL[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]----------------------[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for a BSD-compatible install... /usr/bin/install -c[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether build environment is sane... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for a thread-safe mkdir -p... /bin/mkdir -p[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for gawk... gawk[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether make sets $(MAKE)... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for gcc... gcc[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether the C compiler works... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for C compiler default output file name... a.out[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for suffix of executables... [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether we are cross compiling... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for suffix of object files... o[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether we are using the GNU C compiler... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether gcc accepts -g... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for gcc option to accept ISO C89... none needed[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for style of include used by make... GNU[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking dependency style of gcc... gcc3[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for gcc... gcc[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether we are using the GNU C++ compiler... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking whether gcc accepts -g... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking dependency style of gcc... gcc3[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking how to run the C preprocessor... gcc -E[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for ranlib... ranlib[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking dependency style of gcc... gcc3[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking debug build... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for _aligned_malloc... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for _aligned_free... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for development build...... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking check for sse2...... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for a x86-64 CPU... no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking gtk2+... checking for pkg-config... pkg-config[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking OpenGL... checking for GL/gl.h... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for GL/glu.h... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for GL/glext.h... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lGL... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lGLU... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lGLEW... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking Cg... checking for main in -ljpeg... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lpthread... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lstdc++... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lz... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -ldl... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]checking for main in -lXxf86vm... yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]configure: creating ./config.status[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]config.status: creating Makefile[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]config.status: creating Linux/Makefile[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]config.status: executing depfiles commands[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Configuration:[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Target system type: [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]x86-64 build? no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Debug build? no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Dev build? no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]SSE2 enabled? yes[/FONT][/SIZE]
 
[/FONT]
 
[FONT=Courier New][FONT=Verdana][SIZE=2]Just for grins I tried running the Windows version on a virtual host. It crapped out and told me I didn't have enough resources. I guess that's what happens when I only give it one core to play with![/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Please let me know if more information is needed. TIA for helping a newbie! :)[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Tigerlily[/SIZE][/FONT]
[/FONT][/FONT][/FONT]

---

### Post by daft11 on 2011-07-17
i'm new to using terminal, and have run into some trouble.
there is an error installing the plugins.
any advice?

---

### Post by Perfect Storm on 2011-07-18
> **daft11 said:**
> i'm new to using terminal, and have run into some trouble.
there is an error installing the plugins.
any advice?

Post the terminal in/out-put. Without it we can't know what you're talking about.

---

### Post by Miles_Prower_fr on 2011-08-06
I installed PCSX2 0.9.8 thanks to this PPA:
[https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa](https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa)

Had to install libsoundtouch1c2 prior to this (grabbed a .deb for Lucid here : [http://packages.ubuntu.com/lucid/libsoundtouch1c2](http://packages.ubuntu.com/lucid/libsoundtouch1c2) since it's required and not included in Ubuntu's 11.04 repositories)

Everything installed fine, and the application does run.
However, I do have some performance issues.

Hardware:
- CPU : Intel Core 2 Duo E4600 @ 2,4Ghz (couldn't succeed in overclocking it to 3Ghz in Linux, works fine in Windows though)
- GPU : Nvidia 8500GS
- RAM : 1x 2Gb


When running Shadow of the Colossus with most defaut settings and no speed hacks in Ubuntu and Windows 7 (rendering with OpenGL on both OSes), I notice a HUGE performance gap : 4fps in Ubuntu, 45fps in Windows. How come?

Same thing goes for Dolphin-Emu while running Gamecube games (45fps in Ubuntu, a rock-solid 60fps in Windows 7). I'm a bit disappointed, especially since I don't plan to use Windows at all on this computer (the whole system feels slow, has little space on its partition, is a hassle to deal with and basically provides no fun to work with) and configuring XBMC in Linux as a Home Theatre / Gaming front-end.

I've heard that most people using PCSX2 in Windows are loading up the GSDX10 renderer plugin to speed up things. This plugin allows for a "3X cycle" (?) mode which seems quite efficient. Don't know what it is, but does such a thing exists for the Linux version ?

---

