---
title: "Savage on 8.04"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by filip102 on 2008-05-09
I installed Savage on Ubuntu 8.04 but when I run it, it dont show anything and I can stop it only with killall savage or gnome-terminal.... or X restart :mad:... so how I must install it? Maybe it have something with graphic card, I have Radeon A9250 (I know, old :KS)

On Vista, I can run it..

---

### Post by csi_ on 2008-05-09
First check if you have direct rendering, run:
glxinfo | grep "direct rendering"
Otherwise read: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Then try to install *libtxc-dxtn0*; see [https://launchpad.net/~madman2k/+archive](https://launchpad.net/~madman2k/+archive)

Other solution is to install proprietary driver, but I am not shure if it is supported by your card. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Sockerdrickan on 2008-05-09
Ubuntu 8.10? Blame yourself if something doesn't work then

---

### Post by filip102 on 2008-05-09
Sorry... I instaled it now... I mean 8.04 :lolflag:

---

### Post by Sockerdrickan on 2008-05-09
:lolflag: ok! I get it

---

### Post by eragon100 on 2008-05-09
Well it's working perfectly for me on 8.04

Then again I have:

Intel core 2 duo e6300 @ 1.86 Ghz

1 GB of RAM

512 MB GeForce 7 7500 LE video card

So nothing to spectucalar, but way better than your video card :lolflag:

Anyway, I don't know how to solve it :(

You could try running the windows version under wine, it seems to run great there :)

---

### Post by guildofghostwriters on 2008-05-11
Okay - Ubuntu noob here in need of (and grateful for) help getting this to run. I followed the instructions [here](http://www.newerth.com/wiki/index.php/S1_Installing) which are:

> 1. Download THIS file which contains the standalone Savage package and extract it to a suitable location.

2. Download THIS file which contains the SFE* patch and extract it over the files you extracted in part 1.
   
3. After installing the above file start savage with the script "./Savage"

4. For the manual to savage download THIS file.


SO I extracted the first tar.gz and then I extracted the second tar.gz so that its contents replaced some files from the first file. Now I don't understand what it means by script "./Savage". I've tried cd-ing to the dir where it all is and typing that into the terminal, I've tried clicking a file called savage.sh, I even looked at that file in a text editor and saw something about changing a line so it pointed to the directory where a .bin file was and I did that but all the things I've tried haven't worked. Am I missing a step? When it says in step 3 "After installing the above..." I've assumed that downloading and extracting is the installation or is there more to it than that? Or am I just doing the script ./Savage bit wrong?

Ta in advance for...

---

### Post by Perfect Storm on 2008-05-11
Here's a 64-bit guide: [http://gaming.gwos.org/doku.php/guides:64bit:savage_1](http://gaming.gwos.org/doku.php/guides:64bit:savage_1)

If you're using 32-bit, ignore 
> sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install ia32-libs

---

### Post by Grishka on 2008-05-11
there is a problem with incompatible libpng bundled with the patch. to get Savage to run on Hardy, I had to get and old libpng version from here: [http://packages.ubuntu.com/dapper/i386/libpng12-0/download](http://packages.ubuntu.com/dapper/i386/libpng12-0/download) and unpack the libraries (.so files) into savage/libs folder.

---

### Post by guildofghostwriters on 2008-05-11
Nice one ta very much - those two steps combined did the trick.

---

### Post by filip102 on 2008-05-17
Lol... I run it but I have old graphic card... so i must upgrade.. bt thx 4help :guitar:

---

### Post by iamah on 2008-05-29
Hi, I'm getting this error, on Hardy, used to work fine in previous version... I have my geforce  set up ok...
```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6ba6767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6ba681e]
#2 /usr/lib/libX11.so.6 [0xb770d518]
#3 /usr/lib/libX11.so.6(XUnmapWindow+0x25) [0xb7703ed5]
#4 libs/libSDL-1.2.so.0 [0xb7ebef01]
#5 libs/libSDL-1.2.so.0 [0xb7ec040e]
#6 libs/libSDL-1.2.so.0(SDL_VideoQuit+0x52) [0xb7eb699a]
#7 libs/libSDL-1.2.so.0(SDL_QuitSubSystem+0x8c) [0xb7e98298]
#8 libs/libSDL-1.2.so.0(SDL_Quit+0x20) [0xb7e982ec]
#9 ./silverback.bin [0x80a95d3]
silverback.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Locking assertion failure.  Backtrace:
Segmentation fault

```

---

### Post by iamah on 2008-05-29
> **iamah said:**
> Hi, I'm getting this error, on Hardy, used to work fine in previous version... I have my geforce  set up ok...
```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6ba6767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6ba681e]
#2 /usr/lib/libX11.so.6 [0xb770d518]
#3 /usr/lib/libX11.so.6(XUnmapWindow+0x25) [0xb7703ed5]
#4 libs/libSDL-1.2.so.0 [0xb7ebef01]
#5 libs/libSDL-1.2.so.0 [0xb7ec040e]
#6 libs/libSDL-1.2.so.0(SDL_VideoQuit+0x52) [0xb7eb699a]
#7 libs/libSDL-1.2.so.0(SDL_QuitSubSystem+0x8c) [0xb7e98298]
#8 libs/libSDL-1.2.so.0(SDL_Quit+0x20) [0xb7e982ec]
#9 ./silverback.bin [0x80a95d3]
silverback.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Locking assertion failure.  Backtrace:
Segmentation fault

```

Found the solution, all you have to do is get Savage rid of SDL library. I went to Savages "libs" folder and deleted the SDL lib file, which I don't remember the name but it's pretty obvious.

---

### Post by Xenix on 2008-08-12
> **Grishka said:**
> there is a problem with incompatible libpng bundled with the patch. to get Savage to run on Hardy, I had to get and old libpng version from here: [http://packages.ubuntu.com/dapper/i386/libpng12-0/download](http://packages.ubuntu.com/dapper/i386/libpng12-0/download) and unpack the libraries (.so files) into savage/libs folder.


I am using Ubuntu 8.04.1 32bit and this method does not work for me. I still get the error:- *"PNG header and library versions do not match".* This is after downloading the linked file above and extracting  the .so files in the correct place.

Any advice? I really do like this game and play it every day in Windows. I would really like it to work in Ubuntu again. Works fine for me in Sidux.

---

### Post by Vadi on 2008-08-12
I think you might need to set a variable before launching the game, so that it uses the copied libraries

---

