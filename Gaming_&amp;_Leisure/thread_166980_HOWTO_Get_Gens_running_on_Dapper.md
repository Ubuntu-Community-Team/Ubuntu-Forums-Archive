---
title: "HOWTO: Get Gens running on Dapper"
date: 2006-04-27
forum: Gaming &amp; Leisure
---

### Post by calabris on 2006-04-27
The only Sega Genesis / Megadrive emulator in the repositories right now is DGen, which works well, but lacks a spiffy and user-friendly UI. I wanted something I could put into my Applications menu and have all my Genesis and SegaCD games just a click away. Having used and loved Gens under Windows, I thought I'd try to get it running on Ubuntu. Two hours at the command line later, here's how to do it!

**1. Get Gens source**
Go to [https://sourceforge.net/project/showfiles.php?group_id=73619]("https://sourceforge.net/project/showfiles.php?group_id=73619")
and look in "Gens Source Code" -> "Gens WIP Linux". Download the "gens-rc3.tar.gz" file and extract it.

**2. Get needed build tools**
In order to compile Gens from source, you'll need a few tools installed on your system. Make sure that you have the 'universe' repository enabled in your /etc/apt/sources.list. 
First, make sure you have the right compilers:
```
sudo apt-get install build-essential gcc-3.4 nasm
```

Next, make sure you have the SDL libraries needed:
```
sudo apt-get install libsdl1.2debian-alsa
```
(Note: You may need some of the extra SDL libraries installed - if this does not work, try installing libsdl-gfx, libsdl-image, and libsdl-mixer, along with the '-dev' versions of each package.)

**[UPDATE]** Realized that you'll need dev headers for GTK+ too:
```
sudo apt-get install libgtk2.0-dev
```

**3. Set up your build environment**
Gens WILL NOT COMPILE with the standard gcc-4.0 that comes in Dapper. To make sure that Gens gets built with gcc-3.4, use the following:
```
export CC="gcc-3.4"
```

**4. Build Gens!**
Now that everything is set up, the compilation / install is fairly simple. Go into the directory that you extracted from the .tar.gz, and then:
```
./configure
make
sudo make install
```

Gens will install itself into /usr/local/bin/gens, and you should be able to start the program (or add it to your Applications menu) with just "gens". You will need a BIOS file if you want to play SegaCD games, and to play any games you will of course require legally-acquired ROMs.

Happy Sega-ing!

---

### Post by DoktorSeven on 2006-04-27
I assume these are the old sources; someone has done an update that adds OpenGL support (to make drawing the screen faster than plain SDL, not for 3d effects).  Someone has uploaded sources [here](http://users.vialink.com.br/denilson/gens/). (The 3.5 one is the latest)

(Originally found on the forums of that "other" Linux distro I [won't mention](http://gentoo.org) right [here](http://forums.gentoo.org/viewtopic-t-204287-postdays-0-postorder-asc-start-0.html).)
Performance is significantly better on my machine with the OpenGL version than with plain Gens.

---

### Post by leech on 2006-04-27
Even the RC3.5 is over a year old.  Maybe it's time someone else picks up this project.  By the way, Gens under Linux is WAY faster and runs a whole lot better than Gens under Windows.  It's a lot more stable too, even though it's only a release candidate.  

Anyone know if Ubuntu has fixed their gamepad support yet?  Last time I tried to use it, I still had to do some modprobing and chmoding to get my gamepad to work.  Yet it works flawlessly with Debian Sid...

Leech

---

### Post by DoktorSeven on 2006-04-27
The original Gens project is being massively rewritten, thus the huge delay on even the Windows side:

> 
Gens is now in a sort of "complete rewrite", old sources 2.12b becomes a big mess to maintain and i think it's time to clean all that. Of course you can't expect a new version soon. Even worse, the next version won't have more features that current 2.12b... some will probably miss and others will be added.

(from [http://gens.consolemul.com/](http://gens.consolemul.com/))  

There is a newer fork of it called Gens32 [here](http://gens32.emubase.de/) but it seems to be a Windows-only thing...

---

### Post by shinygerbil on 2006-04-30
When running configure, I get:

```
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK+ version 2.4.0 not found!

```

Now call me silly but I'm sure I have GTK on here. Even though I run KDE.

Anyone know what packages I'm missing?

Cheers

Steve

---

### Post by DoktorSeven on 2006-04-30
You need to install the -dev package as well.  See original post about the GTK dev headers.

---

### Post by shinygerbil on 2006-05-02
Obviously I have already tried that. My post was about GTK+ 2.4.0, about which I find very little mention in Synaptic. The relevant part from my config.log:

```
configure:3409: checking for GTK+ - version >= 2.4.0
configure:3554: result: no
configure:3587: gcc-3.4 -o conftest -g -O2    conftest.c   >&5
conftest.c:13:21: gtk/gtk.h: No such file or directory
conftest.c: In function `main':
conftest.c:19: error: `gtk_major_version' undeclared (first use in this function)
conftest.c:19: error: (Each undeclared identifier is reported only once
conftest.c:19: error: for each function it appears in.)
conftest.c:19: error: `gtk_minor_version' undeclared (first use in this function)
conftest.c:19: error: `gtk_micro_version' undeclared (first use in this function)
configure:3593: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "gens"
| #define VERSION "2.12"
| #define STDC_HEADERS 1
| /* end confdefs.h.  */
| 
| #include <gtk/gtk.h>
| #include <stdio.h>
| 
| int
| main ()
| {
|  return ((gtk_major_version) || (gtk_minor_version) || (gtk_micro_version));
|   ;
|   return 0;
| }
configure:3632: error: *** GTK+ version 2.4.0 not found!

```

So it appears to be looking for a standard GTK+ install and failing to find one.

---

### Post by saVTRonic on 2006-05-02
Same here
```
configure:3409: checking for GTK+ - version >= 2.4.0
configure:3554: result: no
configure:3587: gcc-3.4 -o conftest -g -O2    conftest.c   >&5
conftest.c:13:21: gtk/gtk.h: No such file or directory
conftest.c: In function `main':
conftest.c:19: error: `gtk_major_version' undeclared (first use in this function)
conftest.c:19: error: (Each undeclared identifier is reported only once
conftest.c:19: error: for each function it appears in.)
conftest.c:19: error: `gtk_minor_version' undeclared (first use in this function)
conftest.c:19: error: `gtk_micro_version' undeclared (first use in this function)
configure:3593: $? = 1
```

---

### Post by DoktorSeven on 2006-05-02
Again, have you installed the gtk -dev package?

sudo apt-get install libgtk2.0-dev

---

### Post by GameGod on 2006-05-02
Does Gens have joystick support now?
The last time I tried it (in Breezy), it didn't. :(

---

### Post by DoktorSeven on 2006-05-02
Works fine with my USB gamepad.

---

### Post by saVTRonic on 2006-05-03
[QUOTE=DoktorSeven]Again, have you installed the gtk -dev package?

sudo apt-get install libgtk2.0-dev[/QUOTE]
Yes.

---

### Post by DoktorSeven on 2006-05-03
What does

**pkg-config gtk+-2.0 --cflags**

from the commandline give you?

---

### Post by saVTRonic on 2006-05-03
pkg-config gtk+-2.0 --cflags

```
savtronic@poutre:~$ pkg-config gtk+-2.0 --cflags
Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

```

I have installed "libglitz*-dev".
./configure run well

make :

```
emulator/g_main.c: Dans la fonction «Init» :
emulator/g_main.c:590: attention : incompatible implicit declaration of built-in function «strncpy»
emulator/g_main.c:591: attention : incompatible implicit declaration of built-in function «strcat»
emulator/g_main.c:600: attention : incompatible implicit declaration of built-in function «strcpy»
emulator/g_main.c: Dans la fonction «main» :
emulator/g_main.c:777: attention : incompatible implicit declaration of built-in function «strncpy»
emulator/g_main.c:778: attention : incompatible implicit declaration of built-in function «strcat»
emulator/g_main.c: Hors de toute fonction :
emulator/g_main.c:789: erreur: static declaration of «Build_Language_String» follows non-static declaration
emulator/g_main.c:603: erreur: previous implicit declaration of «Build_Language_String» was here
emulator/g_main.c: Dans la fonction «Build_Language_String» :
emulator/g_main.c:879: attention : incompatible implicit declaration of built-in function «strcpy»
make[3]: *** [emulator/gens-g_main.o] Erreur 1
make[3]: quittant le répertoire « /tmp/gens-rc3.5-opengl/src/gens »
make[2]: *** [all-recursive] Erreur 1
make[2]: quittant le répertoire « /tmp/gens-rc3.5-opengl/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /tmp/gens-rc3.5-opengl »
make: *** [all] Erreur 2

```

---

### Post by saVTRonic on 2006-05-03
[http://www.ubuntuforums.org/showthread.php?t=132561&highlight=gens+opengl](http://www.ubuntuforums.org/showthread.php?t=132561&highlight=gens+opengl)

> (by the way, in order to compile on Ubuntu, you have to remove the "static" on line 787 in /src/gens/emulator/g_main.c)

./configure -> ok
make -> ok
checkinstall -> ok

Gens 3.5 Opengl run well :)

Thanks

Edit : I'm on Dapper + XGL/Compiz (+ Xgame for Opengl games).

---

### Post by psyke83 on 2006-05-05
Hi,

gens-rc3-opengl works at a perfect speed on my laptop (a Dell Inspiron 8000 with ATI Mobility M4, 8mb), but it has some annoying bugs in the GUI and there's a slight graphical problem (a slight black bar). Versions rc3.1 up to rc4 do not work with my card, only a white screen would ever display for opengl. Here's the newest version, rc4 (probably downloaded from cvs) with opengl support: [http://aur.archlinux.org/packages/gens-cvs/gens-cvs/gens-cvs-20050426.tar.bz2](http://aur.archlinux.org/packages/gens-cvs/gens-cvs/gens-cvs-20050426.tar.bz2)

I've created a patch replacing GL_TEXTURE_RECTANGLE_NV with GL_TEXTURE_RECTANGLE in order to make it compatible with my, and possibly other non-NVIDIA cards, which I'll attach to this post. Can someone please build the latest version with my patch and carefully note the speed of emulation? The picture now shows, but I've observed that sound causes a pretty noticeable slowdown (jerky visual scrolling, yet the FPS rate stays around 60). Disabling sound gives a speed of >100fps; the emulation is extremely fast and smooth. My system is most certainly up to the task of emulating a Genesis, the problem I'd say, lies in buggy sound code.

Building is a little tricky, here's the instructions (download gens-cvs-20050426.tar.bz2 and my patch to the same directory before starting):
[LIST]
[*]sudo apt-get install build-essential gcc-3.4 nasm automake1.9 libsdl1.2-dev libgtk2.0-dev
[*]tar jxvf gens-cvs-20050426.tar.bz2
[*][COLOR="Red"]patch -p0 <gens-cvs-nonv.diff.txt[/COLOR]
[*]cd Gens-MultiPlatform/linux
[*]export CC=gcc-3.4
[*]aclocal
[*]sh configure
[*]make
[*]sudo make install
[/LIST]
Can someone help me test this patch? It doesn't matter which graphics card you have, but I would especially recommend those that tried this with an older card such as an ATI Rage 128 (r128 driver), or any card that has the white screen problem. Please, report your experience regarding scrolling speed (e.g., in Sonic 1) with my patch, and test with the sound disabled too (disable while running a game).

If you're interested in the latest version, but don't want to test my patch, just omit the line in red. But I'd be very happy if someone can help me fix this sound problem :)

---

### Post by simplyw00x on 2006-05-06
Great tutorial in the post above; small typo, should be "export CC=gcc**-**3.4"

---

### Post by psyke83 on 2006-05-06
[QUOTE=simplyw00x]Great tutorial in the post above; small typo, should be "export CC=gcc**-**3.4"[/QUOTE]

Thanks, I've corrected that typo and added some packages to install (in case someone didn't install the dev packages already).

---

### Post by saVTRonic on 2006-05-06
[QUOTE=psyke83]
Disabling sound gives a speed of >100fps; the emulation is extremely fast and smooth. My system is most certainly up to the task of emulating a Genesis, the problem I'd say, lies in buggy sound code.[/QUOTE]

Try "Sound/Rate/44100" instead of 22050. It solved the problem for me =)


But i've got another problem :)

```
(gens:10647): Gtk-CRITICAL **: gtk_tree_view_set_model: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gens:10647): Gtk-CRITICAL **: gtk_tree_view_set_model: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gens:10647): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gens:10647): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

```

I can't have the list on the roms in gens.

---

### Post by DoktorSeven on 2006-05-06
I don't see a way to get a ROM list anyway; I always just open directly from File->Open ROM / ctrl+o.

---

### Post by psyke83 on 2006-05-06
[QUOTE=saVTRonic]Try "Sound/Rate/44100" instead of 22050. It solved the problem for me =)[/QUOTE]

Thanks, I already tried that. It's strange, after updating a few packages and recompiling this morning with my patch, the speed is perfect now :). I've enabled VSync, but it has a bug. When you return from fullscreen while a game is running  then go back to fullscreen, VSync gets disabled. You need to press Shift+F3 *twice* while in fullscreen to get VSync working again.

[QUOTE=saVTRonic]I can't have the list on the roms in gens.[/QUOTE]

Sorry, I think that code simply hasn't been implemented fully.

By the way, it seems that this gens will compile fine with gcc4 (which I've done today), perhaps that's what solved my problems...

---

### Post by jon_benge on 2006-05-12
calabris, great tutorial! I am using Breezy Badger so I wasn't sure if your tutorial would work or not.

The only problem I had were the SDL libraries. Installing libsdl1.2debian-alsa made no difference, so I reverted back to the libsdl1.2debian-oss library. I fixed the issue by going into the Synaptic Package Manager and installing the libsdl-dev package!

Gens compiled and installed OK from there :-D 

DoktorSeven, thanks for pointing out the OpenGL version! :-D It has joypad support, unlike other Gens for linux versions that are around

On a side note, if you enable sound then your computer might struggle! To solve this, simply change the frame skip from auto to 2

---

### Post by escape on 2006-05-13
Honestly,  this has worked fine for me in numerous different versions of dapper:
[http://ubuntuforums.org/showthread.php?t=126022&highlight=howto+gens]("http://ubuntuforums.org/showthread.php?t=126022&highlight=howto+gens")

---

### Post by Chrono86 on 2006-08-25
When doing 'make' I get this

> root@adam:~/Desktop/GensForLinux# make
make  all-recursive
make[1]: Entering directory `/home/adam/Desktop/GensForLinux'
Making all in src
make[2]: Entering directory `/home/adam/Desktop/GensForLinux/src'
Making all in starscream
make[3]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream'
Making all in main68k
make[4]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream/main68k'
make  all-am
make[5]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream/main68k'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream/main68k'
Making all in sub68k
make[4]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream/sub68k'
make  all-am
make[5]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream/sub68k'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Entering directory `/home/adam/Desktop/GensForLinux/src/starscream'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream'
make[3]: Leaving directory `/home/adam/Desktop/GensForLinux/src/starscream'
Making all in gens
make[3]: Entering directory `/home/adam/Desktop/GensForLinux/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/sh ../../depcomp \
        /usr/bin/gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/anjuta_widget -I./gtkui/glade -I.   -DDATADIR=\"/usr/local/share/gens\" -I/usr/include/SDL -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -g -O2 -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1].offset')
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1]')gens_core/cpu/68k/cpu_68k.c:28: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for `M68K_Fetch[2].offset')
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for `M68K_Fetch[2]')gens_core/cpu/68k/cpu_68k.c:29: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for `M68K_Fetch[3].offset')
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for `M68K_Fetch[3]')gens_core/cpu/68k/cpu_68k.c:30: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:30: error: (near initialization for `M68K_Fetch[4]')gens_core/cpu/68k/cpu_68k.c:31: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:31: error: (near initialization for `M68K_Fetch[5]')gens_core/cpu/68k/cpu_68k.c:32: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:32: error: (near initialization for `M68K_Fetch[6]')gens_core/cpu/68k/cpu_68k.c:63: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for `S68K_Fetch[0].offset')
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for `S68K_Fetch[0]')gens_core/cpu/68k/cpu_68k.c:64: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:64: error: (near initialization for `S68K_Fetch[1]')gens_core/cpu/68k/cpu_68k.c:65: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:65: error: (near initialization for `S68K_Fetch[2]')gens_core/cpu/68k/cpu_68k.c: In function `M68K_Set_32X_Rom_Bank':
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function `M68K_Set_Prg_Ram':
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[3]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[3]: Leaving directory `/home/adam/Desktop/GensForLinux/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/adam/Desktop/GensForLinux/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/Desktop/GensForLinux'
make: *** [all] Error 2
root@adam:~/Desktop/GensForLinux#


What's wrong?

---

### Post by -DarkMind- on 2006-08-26
please, upload a .deb

---

### Post by hanzomon4 on 2006-08-26
> **-DarkMind- said:**
> please, upload a .deb

Try this one

---

### Post by Lestat1975 on 2006-08-27
I've gotten as far as [gens_core/cpu/68k/gens-cpu_68k.o] Error 1 etc. etc. etc.

I had it running perfectly on Dapper for i386 a few months ago but I decided to try the amd64 flavor because I wanted to see UT2004 64-bit.  I've gotten my xbox360 controller working, xmame, snes9x, and a fewe other things but will keep looking for gens.

---

### Post by hanzomon4 on 2006-08-28
Your xbox360 controller is it a third party controller, I ask because I've been trying for the longest to get to get my Pelican XBOX360 wired T5Z working.

---

### Post by Lestat1975 on 2006-08-28
Sorry but no...my controller is a microsoft controller.

---

### Post by joflow on 2006-09-02
The dpad on my gamepad doesnt work with gens (I used the deb in this thread).  All the other buttons works.  The dpads work with zsnes, so I know its not the hardware.  Anyone have similar issues?

---

### Post by Lestat1975 on 2006-09-07
D-Pad works fine on mine...

Also...I used the gensforlinux_rc3.cvs-1_i386.deb.gz and I did a force install (AMD64) and GENS works like a charm.

---

### Post by disturbedite on 2007-02-09
sorry to revive an old thread, but i wanna compile gens32 for linux but the source the author gave me doesn't work with standard operating procedure:
export CC="gcc-3.4"
./configure
make
install

it doesn't have the required config files let alone the make file.  could someone suggest my next step?

---

### Post by [Jaguar] on 2008-01-17
> **Lestat1975 said:**
> D-Pad works fine on mine...

Also...I used the gensforlinux_rc3.cvs-1_i386.deb.gz and I did a force install (AMD64) and GENS works like a charm.

-BUMP-

How? i'm using the AMD64 Architecture too and it complaints about 'only i386'
help :(

---

