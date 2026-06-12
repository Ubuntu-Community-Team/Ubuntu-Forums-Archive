---
title: "PCSX 0.9.4 Just released..."
date: 2007-11-14
forum: Gaming &amp; Leisure
---

### Post by The Noble on 2007-11-14
As stated in the title, PCSX2 0.9.4 has just been released! This release is showing great promise and should start to become a viable alternative to a PS2 (that is if you have a good computer...), so I think this is a good time to test out the latest release. 

[http://www.pcsx2.net]("http://www.pcsx2.net")

This release supports quite a few playable titles, such as Resident Evil 4, Kingdom Hearts (1 and 2 I believe), Final Fantasy X and XII, and Metal Gear Solid, each at relatively fast speeds, so jump on it! There are more release notes on their site, so what I am summarizing is missing out on quite a few goodies(online play for example).

If you don't understand what it is yet, prepare to be enlightened! Pcsx2 is a playstation 2 emulator, which allows PS2 games to be played on Linux and Windows with a relatively powerful computer. The program is currently in development, so don't expect every random game to work, but as I stated above, many popular titles are fully playable.

That's the good news.

The bad news is that PCSX2 requires* quite a powerful computer to get decent speeds. That means you better have a dual core AMD X2 or Intel C2D above 2.0 GHz, as well as a GPU above or equivalent to an NVidia 6600. This will only garner good speeds on a few games, however, so a faster system is highly recommended for any graphically intensive game. Just a note: to use PCSX2 you need a playstation 2 bios, which should legally be obtained by flashing it from your own playstation.

*I use "required" as in "highly recommended or you are wasting your time". There are no official requirements, so please don't ask.

---

### Post by maduranga on 2007-11-14
Can someone tell me what is this about and how to get it?

---

### Post by The Noble on 2007-11-14
Oh, I totally forgot to give a brief overview! (Which will be added to the first post after this comment)

Pcsx2 is a playstation 2 emulator made by the devs of pcsx, one of the most popular playstation emulators. Essentially, many playstation 2 games can now be played on most current generation Desktops. Currently, I think you have to compile the program, but that has been been covered in the previous PCSX .9.3 release thread I believe.

---

### Post by hikaricore on 2007-11-14
> **maduranga said:**
> Can someone tell me what is this about and how to get it?

Lazy. :lolflag:

---

### Post by Ferrat on 2007-11-14
Well I get it to start ok but for some reason my xbox gamepad (USB) doesn't register at all, anyone got any ideas? tried both plugins and the other gamepad plugins seems only to be .dll files :/

---

### Post by Sockerdrickan on 2007-11-14
Yay netplay

---

### Post by The Noble on 2007-11-14
> **Tux0r said:**
> Yay netplay

From what I understand, the netplay is slightly limited at the moment due to the lack of supported games that play online. I know Monster Hunter and Thirteen play online, so that's two games that work. Netplay requires a newly flashed BIOS IIRC, so downloaded PS2 bios' will only allow the game to be played. This may finally get me to get around to that...

---

### Post by El Lance-O on 2007-11-15
I would absolutely love it if someone could take the time to package this.

I admit I am quite the linux n00b, especially when it comes to compiling, but I have tried over and over and over again with this thing, getting results that aren't anywhere close to what I read about.

It would be a great favor not only to me but to the rest of the Ubuntu community that doesn't have much experience with compiling.

I followed the instructions from the main PCSX2 0.9.3 thread that seems to be the only source of help on this matter. I managed to have 0.9.3 installed, but I don't remember how I did it last time.

It was buggy to say the least, and I wanted to try out the new version.

Please, someone take the time to do this, it would be absolutely fantastic.

I already have all other emulators that I could ever possibly want, and this would really put the icing on the cake.

If this request is too unrealistic, could someone personally walk me through this?

That would also be fantastic.

Thanks ahead of time, hope to get a response soon.

---

### Post by no1wantdthisname on 2007-11-15
I managed to get it to compile and run using this thread:
[http://ubuntuforums.org/showthread.php?t=399165&highlight=pcsx2](http://ubuntuforums.org/showthread.php?t=399165&highlight=pcsx2)

However you will need 2 more packages: libglew-dev and libasound2-dev.

So you will need the following packages to build: 
```
 sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev libglew-dev libasound2-dev libglu1-mesa-dev
```

I managed to get some games to run, but they were all unplayable (too slow).

---

### Post by El Lance-O on 2007-11-15
I got it compiled, but a lot of things still don't work.

It keeps saying my CPU doesn't have MMX support. Funny, seeing as it did fine with the last release.

It also likes to spit random errors at me and suddenly close from time to time.

Compiling has NEVER worked for me.

I guess I'm just not cut out for linux?

---

### Post by Ferrat on 2007-11-15
> **El Lance-O said:**
> I got it compiled, but a lot of things still don't work.

It keeps saying my CPU doesn't have MMX support. Funny, seeing as it did fine with the last release.

It also likes to spit random errors at me and suddenly close from time to time.

Compiling has NEVER worked for me.

I guess I'm just not cut out for linux?


It's just a matter of trial and error before you get it right =) 

And there can be some small stuff making it mess up, I didn't get the grafic plugin to work in the beginning, then I did some looking and found that my libGL.so and some other stuff was linked to files in Panda3D that made pcsx2 read them wrong, just removed the links an d whoho it worked :) 

Got some games working both roms and cds, just not very playable yet ^^

---

### Post by positroniks on 2007-11-16
I downloaded the source from the website, got all dependencies, compiled without errors, and ran the bin. It says it has to be configured, then it says it can't find the plugins directory, I go to browse for them manually and... neither can I :( where is it? Please be aware: I am a linux moron. Only been using it for about a week now.

edit: Nevermind. Apparently the source from the site doesn't inlude the plugins. I also forgot the extra dependencies from above. Installed them and grabbed the source from SVN. Compiled without errors. Now I've just got to dump my bios and I'll try to fire it up :)

edit: Got it up and running... at a snails pace :( Used Front Mission 4 for testing, Ran at an unplayable average of about 7FPS on an AMD 64 X2 4800+ w/ Nvidia 7600GT. For whatever reason CPU config doesn't recognize my Cpu's family or speed features, doesn't save my config settings on reset when trying to enable MTGS, and GPU config tells me that it's not MMX capable, lol. Guess I'll try searching around for more info but it's not looking so good for me.

---

### Post by El Lance-O on 2007-11-16
That described my problems perfectly.

I am using a Nvidia 7300 Go and a Centrino duo core at 3.46 GHz and 1 GB of RAM.

It should work quite swimmingly, but the bios is slow and wouldn't recognize Silent Hill 3. The disk is quite beat up so I will try later with another game if I get the chance, but I don't expect anything at playable speeds.

Should I? I like to think my system isn't too shabby for a laptop.

---

### Post by Soulnet on 2007-11-17
I've managed to compile PCSX2 (from svn with all plugins).
But that error occurs during startup:
**libZeroGSoglr.so.0.96.2 undefined symbol XF86VidModeGetAllModeLines**
and in PCSX2 config window GS Plugin is blank.

Ubuntu 7.10 AMD64 Desktop

---

### Post by NoSmokingBandit on 2007-11-18
Im having a problem with the configuration. None of the Graphics/sound/controller selection boxes have any choices in them. Also when i try to load a bios directory it says "cannot open plugins directory"
I tried running the new version on windows but it was rather slow so i thought i'd try ubuntu but i cant ever get the program configured...

---

### Post by hikaricore on 2007-11-18
> **NoSmokingBandit said:**
> Im having a problem with the configuration. None of the Graphics/sound/controller selection boxes have any choices in them. Also when i try to load a bios directory it says "cannot open plugins directory"
I tried running the new version on windows but it was rather slow so i thought i'd try ubuntu but i cant ever get the program configured...

This has been discussed in a few threads already.
Please search the forums before posting a question in the future.

[http://ubuntuforums.org/showthread.php?p=3792330](http://ubuntuforums.org/showthread.php?p=3792330)

You also should be aware that to get atleast 40-60fps on ANY title you will need atleast a DualCore 2.4ghz processor, a high-end graphics card, and plenty of ram.  Otherwise you're just wasting your time.

---

### Post by gruffy-06 on 2007-11-26
My PC and PS3 can both emulate PS2 games at playable speeds. The odd thing is, although my PC is slower than my PS3, playing PS2 games on my PC feels a lot faster than on the PS3.

---

### Post by ehcualp on 2007-12-03
i get a few errors installing pcsx2:
```

aaron@aaron-desktop:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Linux/Makefile.am:5: shell pkg-config --cflags gtk+-2.0: non-POSIX variable name
Linux/Makefile.am:5: (probably a GNU make extension)
Linux/Makefile.am:6: compiling `callbacks.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
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
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF .deps/libZeroGSLinux_a-callbacks.Tpo -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c
mv -f .deps/libZeroGSLinux_a-callbacks.Tpo .deps/libZeroGSLinux_a-callbacks.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

```
i think i have all the necessary plugins, and libs, but i can't get past this. 
could someone help me?

---

### Post by ehcualp on 2007-12-04
*bump*
i have tried looking around for the answer but have yet to find one. Can somebody help please?

---

### Post by Sarteck on 2007-12-05
```
sudo apt-get install libglew-dev
```

ehcualp, that might work for you--it JUST did for me, same problem.  :)

---

### Post by The Noble on 2007-12-05
Have any of you bothered doing any benchmarks? It would be very interesting to see the difference between windows, linux 686, and linux x86_64... Once my new laptop comes in I may give it a try. But that's if I get around to it.

---

### Post by ehcualp on 2007-12-05
Sarteck, thanks for your response,
i installed libglew-dev, and then i tried compiling it again
heres what came up:
```

aaron@aaron-desktop:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Linux/Makefile.am:5: shell pkg-config --cflags gtk+-2.0: non-POSIX variable name
Linux/Makefile.am:5: (probably a GNU make extension)
Linux/Makefile.am:6: compiling `callbacks.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
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
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF .deps/libZeroGSLinux_a-callbacks.Tpo -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c
mv -f .deps/libZeroGSLinux_a-callbacks.Tpo .deps/libZeroGSLinux_a-callbacks.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
mv -f .deps/libZeroGSLinux_a-Conf.Tpo .deps/libZeroGSLinux_a-Conf.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF .deps/libZeroGSLinux_a-interface.Tpo -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c
mv -f .deps/libZeroGSLinux_a-interface.Tpo .deps/libZeroGSLinux_a-interface.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF .deps/libZeroGSLinux_a-Linux.Tpo -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp
mv -f .deps/libZeroGSLinux_a-Linux.Tpo .deps/libZeroGSLinux_a-Linux.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF .deps/libZeroGSLinux_a-support.Tpo -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c
mv -f .deps/libZeroGSLinux_a-support.Tpo .deps/libZeroGSLinux_a-support.Po
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF .deps/libZeroGSogl_a-GSmain.Tpo -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp
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
make[1]: Leaving directory `/home/aaron/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins

```
i think i got a lot more errors..

---

### Post by ExtremeMultiman on 2007-12-05
Same problem here, same error
I downloaded it from svn then builded. ZeroGSogl plugin is compiled and in the right dir but it just don't work. Some one can resolve this?

---

### Post by Sarteck on 2007-12-05
ehcualp, ExtremeMultiman, did both of you install the nVidia CG Toolkit?

---

### Post by ExtremeMultiman on 2007-12-05
For me sure, downloaded from nvidia site, converted with alien and installed. It won't even compile either

Post edit: Just for further questions: Yes, I have installed necessary libraries. My graphic card has pixel shaders 2.0. My CPU support untile SS3.  I use ubuntu 7.10 on a core 2 duo/centrino Duo T5500 with a 7400 nvidia go. No errors on compiling.

Any advice?

---

### Post by barius on 2007-12-05
> **The Noble said:**
> Have any of you bothered doing any benchmarks? It would be very interesting to see the difference between windows, linux 686, and linux x86_64... Once my new laptop comes in I may give it a try. But that's if I get around to it.

I did a few.
- Windows XP x32 > Linux x32 by a factor of about 20-30% depending on the game.
- Linux x32 = Linux x64

The x32 vs. x64 was disappointing, but I talked with Zerofrog and he tells me that he's concentrating on compatibility right now, speed isn't at the top of his priorities.  I wouldn't expect anything exciting for at least 12 months.

I think it is safe to say that Linux will always be slower than Windows because of the architectural differences between DirectX and OpenGL.  MS has put years of money and effort into making Windows a gaming platform and Linux won't be challenging that any time soon.  However, Zerofrog hasn't put as much work into the OGL plugin as he has the DX plugin so I'm sure there's room for improvement.

---

### Post by barius on 2007-12-05
> **ExtremeMultiman said:**
> For me sure, downloaded from nvidia site, converted with alien and installed. It won't even compile either

Post edit: Just for further questions: Yes, I have installed necessary libraries. My graphic card has pixel shaders 2.0. My CPU support untile SS3.  I use ubuntu 7.10 on a core 2 duo/centrino Duo T5500 with a 7400 nvidia go. No errors on compiling.

Any advice?

Follow this [guide]("http://ubuntuforums.org/showthread.php?t=631979&highlight=PCSX2") and let me know if it helps you.

BTW, if you're wondering why it's in the General forum: 
"it's my first day!" -- Homer Simpson.

---

### Post by ehcualp on 2007-12-05
> **barius said:**
> Follow this [guide]("http://ubuntuforums.org/showthread.php?t=631979&highlight=PCSX2") and let me know if it helps you.

BTW, if you're wondering why it's in the General forum: 
"it's my first day!" -- Homer Simpson.
the nVidia CG Toolkit is what i was missing. thanks, and your guide was helpful too!
all i need to do now is get my ps2 bios...

---

### Post by The Noble on 2007-12-06
> **barius said:**
> I did a few.
- Windows XP x32 > Linux x32 by a factor of about 20-30% depending on the game.
- Linux x32 = Linux x64

The x32 vs. x64 was disappointing, but I talked with Zerofrog and he tells me that he's concentrating on compatibility right now, speed isn't at the top of his priorities.  I wouldn't expect anything exciting for at least 12 months.

I think it is safe to say that Linux will always be slower than Windows because of the architectural differences between DirectX and OpenGL.  MS has put years of money and effort into making Windows a gaming platform and Linux won't be challenging that any time soon.  However, Zerofrog hasn't put as much work into the OGL plugin as he has the DX plugin so I'm sure there's room for improvement.


Sounds interesting...What graphics card do you have by the way? What games did you test? I would guess that the DX -> OGL slowdown would only effect games like RE4 which are GPU intensive. If Something like FFX had the same problem, then there is something wrong with their port. Not to worry though, .9.3 was more of a stopgap to get to .9.4, and there is quite a bit of optimization that can probably be squeezed yet! 

Another question: did you ever contact Refraction (or whoever does the central coding for PCSX2) about the discrepancies? It would be interesting to se where the problems lie. Thanks for replying.

---

### Post by ExtremeMultiman on 2007-12-06
> **barius said:**
> Follow this [guide]("http://ubuntuforums.org/showthread.php?t=631979&highlight=PCSX2") and let me know if it helps you.

BTW, if you're wondering why it's in the General forum: 
"it's my first day!" -- Homer Simpson.

Don't which package I missed, anyway even if compiplation log didn't change one of the apt-get made the difference, thank you

---

### Post by barius on 2007-12-06
> **The Noble said:**
> Sounds interesting...What graphics card do you have by the way? What games did you test?
...
Another question: did you ever contact Refraction (or whoever does the central coding for PCSX2) about the discrepancies? It would be interesting to se where the problems lie. Thanks for replying.

I have an Nvidia 8800GTS 320Mb, my CPU is an E6600@3.0Ghz and I have 2Gb of 800Mhz RAM@1050Mhz.  I tested Disgaea (2D), FFX (3D fast) and RE4 (3D slow).  They were all about 20-30% off from Windows so I think the biggest bottleneck is the emulator itself, not the GS.

NOTE, however, that I was testing the best Windows config against the best Linux config.  That is, I used the DX version of ZeroGS and the VM version of PCSX2 in Windows.  Neither of these options is available for Linux and I think the biggest problem lies in the lack of a VM implementation for Linux.

No, I did not talk with Refraction about it.  I don't think he would be interested by it unless you could also provide code examples of how to improve it.  He's got better things to do than try to explain things to newbs ;)
I only spoke about it briefly with Zerofrog because I had done some work to improve the OGL GS plugin and we got into a bit of a discussion about it.

---

### Post by The Noble on 2007-12-09
> **barius said:**
> I have an Nvidia 8800GTS 320Mb, my CPU is an E6600@3.0Ghz and I have 2Gb of 800Mhz RAM@1050Mhz.  I tested Disgaea (2D), FFX (3D fast) and RE4 (3D slow).  They were all about 20-30% off from Windows so I think the biggest bottleneck is the emulator itself, not the GS.

NOTE, however, that I was testing the best Windows config against the best Linux config.  That is, I used the DX version of ZeroGS and the VM version of PCSX2 in Windows.  Neither of these options is available for Linux and I think the biggest problem lies in the lack of a VM implementation for Linux.

No, I did not talk with Refraction about it.  I don't think he would be interested by it unless you could also provide code examples of how to improve it.  He's got better things to do than try to explain things to newbs ;)
I only spoke about it briefly with Zerofrog because I had done some work to improve the OGL GS plugin and we got into a bit of a discussion about it.

Ah, Intriguing. That makes sense. I just wanted to make sure that they were aware of the inconsistencies. I'm actually building pcsx2 right now, and I would be extremely pleased if FFX plays well on my new laptop (1.8 Ghz C2D with 8400 GS). Thanks for the nugget of wisdom; it's why I even bother to read their forums anymore.

---

### Post by go_beep_yourself on 2007-12-12
> **El Lance-O said:**
> I got it compiled, but a lot of things still don't work.

It keeps saying my CPU doesn't have MMX support. Funny, seeing as it did fine with the last release.

It also likes to spit random errors at me and suddenly close from time to time.

Compiling has NEVER worked for me.

I guess I'm just not cut out for linux?

To find out if your cpu has mmx support, try this. If you get no output, then you don't have it.

```
chris@ubuntu:~$ cat /proc/cpuinfo | grep -i mmx
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
chris@ubuntu:~$ 
```

---

### Post by ehcualp on 2007-12-13
i finally got my ps2 bios, and i play a few of my games
Most of which are unplayble because of speed issues.
i have a amd athlon 64 x2 4600+ with 2 gb of ddr2 ram.

---

### Post by go_beep_yourself on 2007-12-13
> **ehcualp said:**
> i finally got my ps2 bios, and i play a few of my games
Most of which are unplayble because of speed issues.
i have a amd athlon 64 x2 4600+ with 2 gb of ddr2 ram.

Are you sure it's not your video card that is slowing it down?

---

### Post by ehcualp on 2007-12-13
> **go_beep_yourself said:**
> Are you sure it's not your video card that is slowing it down?

im not sure. I have a 7600 gs. I plan on upgrading very soon.

---

### Post by garytr23 on 2007-12-27
> **Soulnet said:**
> I've managed to compile PCSX2 (from svn with all plugins).
But that error occurs during startup:
**libZeroGSoglr.so.0.96.2 undefined symbol XF86VidModeGetAllModeLines**
and in PCSX2 config window GS Plugin is blank.

Ubuntu 7.10 AMD64 Desktop

I had the same problem, I needed to do a 
"sudo apt-get install libxxf86vm-dev" to get rid of it.  Looks like it compiles but doesn't know what to link against.

---

### Post by joereith on 2007-12-27
how do i remove pcsx2 from my computer?????????????

---

