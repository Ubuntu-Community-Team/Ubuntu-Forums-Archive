---
title: "[SOLVED] Need help installing Daimonin"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by Sceiron on 2008-02-29
I'm trying to install Daimonin.

I DLed the client file from their web.site and extracted it.
Then i tried to run ```
 sh ./configure
``` 
but it was complaining about missing dependencies... so i went in synaptic and marked out the following for installation.
ibsdl1.2debian
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-mixer1.2-dev

This took care of the SDL problems i assume.

This brought me a step closer, then i run 
```
 sh ./configure
```
again.
The terminal puts out:
```
sceiron@gutsy:~/Games/Daimonin/client/make/linux$ sh ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether gcc and cc understand -c and -o together... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for cp... /bin/cp
checking for rm... /bin/rm
checking for rmdir... /bin/rmdir
checking for mkdir... /bin/mkdir
checking for sdl-config... /usr/bin/sdl-config
checking for IMG_Load in -lSDL_image... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for PHYSFS_init in -lphysfs... no
configure: error: PhysicsFS lib not found! Get PhysicsFS from http://icculus.org/physfs/
sceiron@gutsy:~/Games/Daimonin/client/make/linux$ 

```
well, i went back in synaptic and marked out libphysfs-1.0-0 and installed the package. But again i get the same error when trying to run configure.
Synaptic says that lphysfs verison 1.0.0-5 is intalled.

Could it be the wrong verison of the package ?
Or is it the wrong package ?
I'm lost here.... any help would be much appreciated.
Sceiron



EDIT: This is what i have to do, how do i do it ?
> Alderan: Also you need the physfs library and libcurl:
[http://icculus.org/physfs/](http://icculus.org/physfs/)
libcurl, libcurl-dev or libcurl-devel are avaible for all distros

---

### Post by Sceiron on 2008-03-03
- bump -

---

### Post by Perfect Storm on 2008-03-03
```
sudo aptitude install libphysfs-**dev**
```

When compiling you need the -dev packages,

---

### Post by Sceiron on 2008-03-03
Thanks a lot AI.
That helped me with the install issue :D
```
*** Daimonin client successful installed in /home/sceiron/daimonin-0.9.7!
*** Enter your install folder and type ./daimonin
*** to start the game!
make[2]: Leaving directory `/home/sceiron/Games/Daimonin/client/make/linux'
make[1]: Leaving directory `/home/sceiron/Games/Daimonin/client/make/linux'
sceiron@gutsy:~/Games/Daimonin/client/make/linux$ ./daimonin
Can't find file settings/options.dat. Using defaults.
load_interface_file(): Can't find file settings/interface.gui.
..Can't open/load the interface file - settings/interface.gui. Resetting..
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
Defaultskin (skins/subred.zip) not found. Your client will most likely crash!
PHYSFS: skins/subred not found.
PHYSFS_addPath facepack.zip failed: File not found
PHYSFS_addPath4 failed: File not found
List Video Modes
All resolutions available.
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no
VideoInfo: video memory: 0KB
Could not load skin-definition for skin: subred.
Reason: No such file or directory
Using defaults.
file: bitmaps/palette.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/palette.png
load_bitmap(): Can't load bitmap bitmaps/palette.png
file: bitmaps/font7x4.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font7x4.png
load_bitmap(): Can't load bitmap bitmaps/font7x4.png
file: bitmaps/font6x3out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap bitmaps/font6x3out.png
file: bitmaps/font_big.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font_big.png
load_bitmap(): Can't load bitmap bitmaps/font_big.png
file: bitmaps/font7x4out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap bitmaps/font7x4out.png
file: bitmaps/font11x15.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font11x15.png
load_bitmap(): Can't load bitmap bitmaps/font11x15.png
file: bitmaps/font11x15out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font11x15out.png
load_bitmap(): Can't load bitmap bitmaps/font11x15out.png
file: bitmaps/intro.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/intro.png
load_bitmap(): Can't load bitmap bitmaps/intro.png
Segmentation fault (core dumped)
```

Now the game wont start.
To me it seems like there is something missing in the pfysfs library but i really dont know....
Any suggestions on what the problem is ?

EDIT: lol, stupid me, had to change folder to launch the game from.... It WORKS now :D

---

