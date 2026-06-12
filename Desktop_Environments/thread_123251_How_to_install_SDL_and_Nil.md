---
title: "How to install SDL and Nil"
date: 2006-01-29
forum: Desktop Environments
---

### Post by El Kabong on 2006-01-29
Hey everyone, I have another problem. I'm trying to install the game Nil (Nil isn't Liero) on my machine. I got the nil-cvs-backup-20050603-1400.tar.bz2 file, and extracted it to my desktop. I opened the terminal, and cd'd into the /home/username/Desktop/nil folder. Once there, I ran ./configure. However, after it was done, it said I need the SDL library installed, and told me to go to [www.libsdl.org](www.libsdl.org) to get it. I then downloaded the SDL-1.2.9.tar.gz file. However, I'm not sure where to go from there. I extracted it, and entered the folder. Once there, I ran ./configure again. From here, I'm lost. Have any of yall ever ran into this problem? Where do I go from here? Thanks ahead of time for any help!

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=El Kabong]Hey everyone, I have another problem. I'm trying to install the game Nil (Nil isn't Liero) on my machine. I got the nil-cvs-backup-20050603-1400.tar.bz2 file, and extracted it to my desktop. I opened the terminal, and cd'd into the /home/username/Desktop/nil folder. Once there, I ran ./configure. However, after it was done, it said I need the SDL library installed, and told me to go to [www.libsdl.org](www.libsdl.org) to get it. I then downloaded the SDL-1.2.9.tar.gz file. However, I'm not sure where to go from there. I extracted it, and entered the folder. Once there, I ran ./configure again. From here, I'm lost. Have any of yall ever ran into this problem? Where do I go from here? Thanks ahead of time for any help![/QUOTE]
Did you try getting one of the libsdl*-dev packages from the repositories first?  They set themselves up automatically, so you don't need to worry about the configuration.

---

### Post by stalefries on 2006-01-29
Try "apt-cache search libsdl dev". Then use "sudo apt-get install <list programs here>" to install thos programs.

---

### Post by El Kabong on 2006-01-29
no, I haven't... how would I go about doing that? Sorry, but I'm very new to linux/ubuntu

---

### Post by El Kabong on 2006-01-29
*bump*

---

### Post by RAOF on 2006-01-29
[QUOTE=El Kabong]*bump*[/QUOTE]
Go to Synaptic (System -> Administration -> Synaptic Package Manager).
Hit "search".
Enter "libsdl"
Find the package named "libsdl-dev"
Mark it for installation.
Hit "apply"
Tada!  You're done.

---

### Post by El Kabong on 2006-01-29
Thanks for the reply RAOF, this isn't the first time you've saved my butt! Okay, I installed the sdl thing you said, and I went to the folder that the "nil" game that I want is in, and ran ./configure... this is what I got:

+-------------------------------------------------------+
I         NiL isn't Liero - configure script            I
I            written by Christoph Brill                 I
+-------------------------------------------------------+
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring NiL

Check system: ubuntu - Linux
Checking for: g++       /usr/bin/g++
Checking for: make      /usr/bin/make
Checking for: ar        /usr/bin/ar
Checking for: ld        /usr/bin/ld
Checking for: ranlib    /usr/bin/ranlib
Checking for: rm        /bin/rm
Checking for: strip     /usr/bin/strip
Checking for: uname     /bin/uname
Checking for: stdc++            found
Checking for: libSDL            found
Checking for: sdl-config        /usr/bin/sdl-config
Checking for: SDL_mixer         not found

ERROR: You need the SDL_mixer enhancement for the SDL library installed.
ERROR: Take a look at [http://www.libsdl.org/projects/SDL_mixer/](http://www.libsdl.org/projects/SDL_mixer/) to get it.

It seems that your system doesn't support compilation.
If you are missing a binary or a library, try to install
the needed dependencies. If another error occurs, contact
me at this address : <nil-devel@lists.sourceforge.net>
Exiting.
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring utils

---------------------------------------------------------
 configuring rgbf<->png converter

Check system: ubuntu - Linux
Building Makefile...
./configure: line 30: Makefile: Permission denied
./configure: line 31: Makefile: Permission denied
./configure: line 32: Makefile: Permission denied
./configure: line 33: Makefile: Permission denied
./configure: line 34: Makefile: Permission denied
./configure: line 35: Makefile: Permission denied
./configure: line 36: Makefile: Permission denied
./configure: line 37: Makefile: Permission denied
./configure: line 38: Makefile: Permission denied
./configure: line 39: Makefile: Permission denied
./configure: line 40: Makefile: Permission denied
./configure: line 41: Makefile: Permission denied
./configure: line 42: Makefile: Permission denied
./configure: line 43: Makefile: Permission denied
./configure: line 44: Makefile: Permission denied
./configure: line 45: Makefile: Permission denied
./configure: line 46: Makefile: Permission denied
./configure: line 47: Makefile: Permission denied
./configure: line 48: Makefile: Permission denied
./configure: line 49: Makefile: Permission denied
./configure: line 50: Makefile: Permission denied
./configure: line 51: Makefile: Permission denied
./configure: line 14: Makefile: Permission denied
./configure: line 15: Makefile: Permission denied
./configure: line 16: Makefile: Permission denied
./configure: line 17: Makefile: Permission denied
./configure: line 25: Makefile: Permission denied
./configure: line 27: Makefile: Permission denied
./configure: line 28: Makefile: Permission denied
./configure: line 29: Makefile: Permission denied
./configure: line 30: Makefile: Permission denied
./configure: line 31: Makefile: Permission denied
./configure: line 32: Makefile: Permission denied
./configure: line 33: Makefile: Permission denied
./configure: line 34: Makefile: Permission denied
./configure: line 35: Makefile: Permission denied
./configure: line 36: Makefile: Permission denied
./configure: line 37: Makefile: Permission denied
./configure: line 38: Makefile: Permission denied
./configure: line 39: Makefile: Permission denied
./configure: line 40: Makefile: Permission denied
./configure: line 41: Makefile: Permission denied
./configure: line 42: Makefile: Permission denied
./configure: line 43: Makefile: Permission denied
./configure: line 44: Makefile: Permission denied
./configure: line 45: Makefile: Permission denied
./configure: line 46: Makefile: Permission denied
./configure: line 47: Makefile: Permission denied
./configure: line 48: Makefile: Permission denied
./configure: line 49: Makefile: Permission denied
./configure: line 50: Makefile: Permission denied
./configure: line 51: Makefile: Permission denied
./configure: line 52: Makefile: Permission denied
Building Makefile...
./configure: line 14: Makefile: Permission denied
./configure: line 15: Makefile: Permission denied
./configure: line 16: Makefile: Permission denied
./configure: line 17: Makefile: Permission denied
./configure: line 18: Makefile: Permission denied
./configure: line 19: Makefile: Permission denied
./configure: line 20: Makefile: Permission denied
./configure: line 21: Makefile: Permission denied

 done configuring utils
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
./configure: line 20: Makefile: Permission denied
./configure: line 21: Makefile: Permission denied
./configure: line 22: Makefile: Permission denied
./configure: line 23: Makefile: Permission denied
./configure: line 24: Makefile: Permission denied
./configure: line 25: Makefile: Permission denied
./configure: line 26: Makefile: Permission denied
./configure: line 27: Makefile: Permission denied
./configure: line 28: Makefile: Permission denied
./configure: line 29: Makefile: Permission denied
./configure: line 30: Makefile: Permission denied
=========================================================
Configure script successfully ended.

Now, type "make" for compiling the software.



okay, what does this mean? sorry to be so in the dark about this...

---

### Post by RAOF on 2006-01-29
I'd guess the problem is the

Checking for: SDL_mixer not found

line.  You should probably install the libsdl-mixer1.2-dev package, then try again.

---

### Post by El Kabong on 2006-01-29
okay, I installed that, and then ran it again. It was missing a few other things, so I went and installed them all. Now, when I run ./configure, I get:

+-------------------------------------------------------+
I         NiL isn't Liero - configure script            I
I            written by Christoph Brill                 I
+-------------------------------------------------------+
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring NiL

Check system: ubuntu - Linux
Checking for: g++       /usr/bin/g++
Checking for: make      /usr/bin/make
Checking for: ar        /usr/bin/ar
Checking for: ld        /usr/bin/ld
Checking for: ranlib    /usr/bin/ranlib
Checking for: rm        /bin/rm
Checking for: strip     /usr/bin/strip
Checking for: uname     /bin/uname
Checking for: stdc++            found
Checking for: libSDL            found
Checking for: sdl-config        /usr/bin/sdl-config
Checking for: SDL_mixer         found
Checking for: SDL_ttf           found
Checking for: SDL_image         found
Checking for: libz              found
Checking for: libbz2 (optional) not found

Checking for: pthread           found
Building Makefile...

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring utils

---------------------------------------------------------
 configuring rgbf<->png converter

Check system: ubuntu - Linux
Building Makefile...
./configure: line 30: Makefile: Permission denied
./configure: line 31: Makefile: Permission denied
./configure: line 32: Makefile: Permission denied
./configure: line 33: Makefile: Permission denied
./configure: line 34: Makefile: Permission denied
./configure: line 35: Makefile: Permission denied
./configure: line 36: Makefile: Permission denied
./configure: line 37: Makefile: Permission denied
./configure: line 38: Makefile: Permission denied
./configure: line 39: Makefile: Permission denied
./configure: line 40: Makefile: Permission denied
./configure: line 41: Makefile: Permission denied
./configure: line 42: Makefile: Permission denied
./configure: line 43: Makefile: Permission denied
./configure: line 44: Makefile: Permission denied
./configure: line 45: Makefile: Permission denied
./configure: line 46: Makefile: Permission denied
./configure: line 47: Makefile: Permission denied
./configure: line 48: Makefile: Permission denied
./configure: line 49: Makefile: Permission denied
./configure: line 50: Makefile: Permission denied
./configure: line 51: Makefile: Permission denied
./configure: line 14: Makefile: Permission denied
./configure: line 15: Makefile: Permission denied
./configure: line 16: Makefile: Permission denied
./configure: line 17: Makefile: Permission denied
./configure: line 25: Makefile: Permission denied
./configure: line 27: Makefile: Permission denied
./configure: line 28: Makefile: Permission denied
./configure: line 29: Makefile: Permission denied
./configure: line 30: Makefile: Permission denied
./configure: line 31: Makefile: Permission denied
./configure: line 32: Makefile: Permission denied
./configure: line 33: Makefile: Permission denied
./configure: line 34: Makefile: Permission denied
./configure: line 35: Makefile: Permission denied
./configure: line 36: Makefile: Permission denied
./configure: line 37: Makefile: Permission denied
./configure: line 38: Makefile: Permission denied
./configure: line 39: Makefile: Permission denied
./configure: line 40: Makefile: Permission denied
./configure: line 41: Makefile: Permission denied
./configure: line 42: Makefile: Permission denied
./configure: line 43: Makefile: Permission denied
./configure: line 44: Makefile: Permission denied
./configure: line 45: Makefile: Permission denied
./configure: line 46: Makefile: Permission denied
./configure: line 47: Makefile: Permission denied
./configure: line 48: Makefile: Permission denied
./configure: line 49: Makefile: Permission denied
./configure: line 50: Makefile: Permission denied
./configure: line 51: Makefile: Permission denied
./configure: line 52: Makefile: Permission denied
Building Makefile...
./configure: line 14: Makefile: Permission denied
./configure: line 15: Makefile: Permission denied
./configure: line 16: Makefile: Permission denied
./configure: line 17: Makefile: Permission denied
./configure: line 18: Makefile: Permission denied
./configure: line 19: Makefile: Permission denied
./configure: line 20: Makefile: Permission denied
./configure: line 21: Makefile: Permission denied

 done configuring utils
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
./configure: line 20: Makefile: Permission denied
./configure: line 21: Makefile: Permission denied
./configure: line 22: Makefile: Permission denied
./configure: line 23: Makefile: Permission denied
./configure: line 24: Makefile: Permission denied
./configure: line 25: Makefile: Permission denied
./configure: line 26: Makefile: Permission denied
./configure: line 27: Makefile: Permission denied
./configure: line 28: Makefile: Permission denied
./configure: line 29: Makefile: Permission denied
./configure: line 30: Makefile: Permission denied
=========================================================
Configure script successfully ended.

Now, type "make" for compiling the software.


I'm guessing that it's not supposed to say "Permission Denied" like that... any ideas? Thanks again

---

### Post by RAOF on 2006-01-29
Maybe the configure script is a bit broken.  You could try running "sudo ./configure" to give configure root privs, but it shouldn't need them.

---

### Post by El Kabong on 2006-01-29
Okay, I tried it with sudo, and I got this:
+-------------------------------------------------------+
I         NiL isn't Liero - configure script            I
I            written by Christoph Brill                 I
+-------------------------------------------------------+
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring NiL

Check system: ubuntu - Linux
Checking for: g++       /usr/bin/g++
Checking for: make      /usr/bin/make
Checking for: ar        /usr/bin/ar
Checking for: ld        /usr/bin/ld
Checking for: ranlib    /usr/bin/ranlib
Checking for: rm        /bin/rm
Checking for: strip     /usr/bin/strip
Checking for: uname     /bin/uname
Checking for: stdc++            found
Checking for: libSDL            found
Checking for: sdl-config        /usr/bin/sdl-config
Checking for: SDL_mixer         found
Checking for: SDL_ttf           found
Checking for: SDL_image         found
Checking for: libz              found
Checking for: libbz2 (optional) not found

Checking for: pthread           found
Building Makefile...

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 configuring utils

---------------------------------------------------------
 configuring rgbf<->png converter

Check system: ubuntu - Linux
Building Makefile...
Building Makefile...

 done configuring utils
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
=========================================================
Configure script successfully ended.

Now, type "make" for compiling the software.


Unless I'm mistaken, that seemed to work. If it looks like it did, can you please point me in the direction of what I'm supposed to do now? I have never compiled anything before, and I'm not sure what to do or where to do it... Thanks a ton, again for saving my butt!

---

### Post by RAOF on 2006-01-29
Like it says, now type "make" to compile the program(s).

Then you can probably run "sudo make install" to copy the program files to appropriate directories.

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=RAOF]Like it says, now type "make" to compile the program(s).

Then you can probably run "sudo make install" to copy the program files to appropriate directories.[/QUOTE]
You might want to get the checkinstall package and "sudo checkinstall -D" instead.  That will let you uninstall the game later if you need to.

---

### Post by El Kabong on 2006-01-29
okay, how do I know where I'm supposed to copy the files? Do I just put them wherever I want them to be?

---

### Post by RAOF on 2006-01-29
[QUOTE=El Kabong]okay, how do I know where I'm supposed to copy the files? Do I just put them wherever I want them to be?[/QUOTE]
You're not.  You don't need to know.  That's what "sudo make install" or, equivalently, "sudo checkinstall" do - they copy them automatically to where they're meant to be.  The "sudo checkinstall" one also adds the program to your list of programs in synaptic, so you can remove it later.

---

### Post by El Kabong on 2006-01-29
oh, ok... I understand now. Once I finish all that stuff, will the game be available in a menu, or will I have to do something else to be able to use it?

I guess what I mean is, once I do the sudo make install deal, am I done?

---

### Post by RAOF on 2006-01-29
[QUOTE=El Kabong]oh, ok... I understand now. Once I finish all that stuff, will the game be available in a menu, or will I have to do something else to be able to use it?

I guess what I mean is, once I do the sudo make install deal, am I done?[/QUOTE]
You **should** be done.  make install should add a menu item, if appropriate.

---

### Post by El Kabong on 2006-01-29
lol I'm sorry to be such a bother to you, I really appreciate you helping me out like this. Linux is pretty hard for a windows man to get used to! Okay now do I just run "sudo make install" when I'm in the folder of the game? Or does it have to be "sudo make install nil"?

---

### Post by RAOF on 2006-01-29
Just "sudo make install".

---

### Post by El Kabong on 2006-01-29
okay, I ran "make" and it gave me this:

make[1]: Entering directory `/home/mchaney2/Desktop/nil/src'
Cleaning up nil : ok

Compiling nil_main.cpp : ok

Creating libsd_threads.a library : Created with warnings :
/usr/bin/ar: creating libsd_threads.a
Generating archive index : ok

Compiling client/animation/animation.cpp : ok
Compiling client/animation/animations.cpp : ok
Compiling client/animation/animator.cpp : ok
Compiling client/animation/anim_helpers.cpp : ok
Compiling client/bot.cpp : ok
Compiling client/chat.cpp : ok
Compiling client/clientworld.cpp : ok
Compiling client/console/nil_console.cpp : ok
Compiling client/controls/controls.cpp : ok
Compiling client/controls/keymapper_bindings.cpp : ok
Compiling client/controls/keymapper.cpp : ok
Compiling client/event/event.cpp : ok
Compiling client/event/event_joystick.cpp : ok
Compiling client/event/event_keyboard.cpp : ok
Compiling client/event/event_mouse.cpp : ok
Compiling client/event/event_target.cpp : ok
Compiling client/fonts/font_instance.cpp : Creation failed :
client/fonts/font_instance.cpp: In member function &#8216;bool Font_instance::load(Loader*, char*, int32)&#8217;:
client/fonts/font_instance.cpp:71: error: &#8216;TTF_OpenFontRW&#8217; was not declared in this scope
make[1]: *** [client/fonts/font_instance.o] Error 1
make[1]: Leaving directory `/home/mchaney2/Desktop/nil/src'
make: *** [nil] Error 2

what do you think that means?

---

### Post by RAOF on 2006-01-29
I think that means that it hasn't configured itself properly.  Short of actually downloading the game & trying to install it, there's not much I can do to help you there.  Try contacting the developers of the game/look at the website for it/forums for it, see if this is a known issue, whether there are any work-arounds, etc.

---

### Post by El Kabong on 2006-01-30
okay... thanks again for all your help!

---

### Post by El Kabong on 2006-01-30
okay, I tried to do the make command again, and it said that "make" is up to date. So I tried to do "sudo checkinstall -D", and it said:

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


is it basically just FUBAR? or is it fixable?

---

### Post by El Kabong on 2006-01-30
*bump*

---

### Post by RAOF on 2006-01-30
[QUOTE=El Kabong]...
is it basically just FUBAR? or is it fixable?[/QUOTE]
Essentially FUBAR: Fixable, but will require knowledge of the code/programming to fix.  Ask the developers of the game/any forums the game has.

---

### Post by El Kabong on 2006-01-30
okay, will do. Thanks again, just wanted to make sure!

---

### Post by nata.loko on 2006-03-31
I'm new in Linux, I'm trying to install Nil, but I cant...

I write ./configure && make


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for awk... awk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.0.0... yes
checking for main in -lSDL_mixer... yes
checking for main in -lSDL_image... yes
checking for main in -lSDL_ttf... yes
checking for main in -lz... yes
checking for main in -lpthread... yes
checking for atexit... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for memset... yes
checking for rint... yes
checking for select... yes
checking for socket... yes
checking for sqrt... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strtol... yes
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for error_at_line... yes
checking for pid_t... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... (cached) yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether setvbuf arguments are reversed... no
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for vprintf... yes
checking for _doprnt... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for off_t... yes
checking for pid_t... (cached) yes
checking return type of signal handlers... void
checking for size_t... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating nil/Makefile
config.status: creating nil/docs/Makefile
config.status: creating nil/docs/en/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/nata/nil/nil'
Making all in nil
make[2]: Entering directory `/home/nata/nil/nil/nil'
Making all in docs
make[3]: Entering directory `/home/nata/nil/nil/nil/docs'
Making all in en
make[4]: Entering directory `/home/nata/nil/nil/nil/docs/en'
make[4]: No se hace nada para `all'.
make[4]: Leaving directory `/home/nata/nil/nil/nil/docs/en'
make[4]: Entering directory `/home/nata/nil/nil/nil/docs'
make[4]: No se hace nada para `all-am'.
make[4]: Leaving directory `/home/nata/nil/nil/nil/docs'
make[3]: Leaving directory `/home/nata/nil/nil/nil/docs'
make[3]: Entering directory `/home/nata/nil/nil/nil'
source='raw_surface.cpp' object='raw_surface.o' libtool=no \
depfile='.deps/raw_surface.Po' tmpdepfile='.deps/raw_surface.TPo' \
depmode=gcc3 /bin/sh ../depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/include/SDL -D_REENTRANT  -g -O2 -c -o raw_surface.o `test -f 'raw_surface.cpp' || echo './'`raw_surface.cpp
raw_surface.cpp: In function ‘void draw_stretch(const Raw_surface*, Mutable_raw_surface*, int, int, int, int, int, int, int, const BlendFunc&)’:
raw_surface.cpp:379: error: ‘const class Raw_surface’ no tiene un miembro llamado ‘_get_xsize’
raw_surface.cpp:382: error: ‘xsize’ no se declaró en este ámbito
make[3]: *** [raw_surface.o] Error 1
make[3]: Leaving directory `/home/nata/nil/nil/nil'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nata/nil/nil/nil'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nata/nil/nil'
make: *** [all] Error 2



What's wrong? What can I do? ](*,) 

Thanks

---

### Post by Peturrr on 2006-04-03
After wrestling with this cool game, I finally managed to compile this one!!
I will try to compile the newest svn version too, and after that I will post a complete Howto.

[edit]
well, that new one didn't work for me. I Guess we wil need to wait for the authors to come up with a release. 

There is a new wiki created at [http://nil.sourceforge.net/wiki/index.php/](http://nil.sourceforge.net/wiki/index.php/) with some recent new etc. Looks like the project isn't dead after all and will be developed further.

---

### Post by Zangdar on 2006-04-03
Which repositry do I need in order to install libsdl1.2-dev
because apt-get can't find it.

Thanks.

---

### Post by Txukie on 2006-04-18
It is in main so you should be able to see it. Use synaptic it might be easier.
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibs%2Flibsdl1.2%2Flibsdl1.2-dev_1.2.7%2B1.2.8cvs20041007-5.3ubuntu2_i386.deb&md5sum=97aa5abd72e71ad1ef83a94e8512828c&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibs%2Flibsdl1.2%2Flibsdl1.2-dev_1.2.7%2B1.2.8cvs20041007-5.3ubuntu2_i386.deb&md5sum=97aa5abd72e71ad1ef83a94e8512828c&arch=i386&type=main)

---

### Post by jon_benge on 2006-05-12
[QUOTE=RAOF]Go to Synaptic (System -> Administration -> Synaptic Package Manager).
Hit "search".
Enter "libsdl"
Find the package named "libsdl-dev"
Mark it for installation.
Hit "apply"
Tada!  You're done.[/QUOTE]

RAOF, you're a star :-D  I was trying to compile a different program and this post solved my problem. Cheers!

---

