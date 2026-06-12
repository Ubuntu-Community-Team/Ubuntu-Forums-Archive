---
title: "could someone please post a step by step guide to install NESTOPIA???"
date: 2009-04-24
forum: Gaming &amp; Leisure
---

### Post by stayfly on 2009-04-24
I'd really appreciate it if someone could please post a simple, step by step guide to install Nestopia on Ubuntu

anyone?

---

### Post by compiledkernel on 2009-04-24
Does not GFceu provide the same functionality that Nestopia does? 

It is in the repos and on g-a-i.

---

### Post by mysoogal on 2009-04-24
> **stayfly said:**
> I'd really appreciate it if someone could please post a simple, step by step guide to install Nestopia on Ubuntu

anyone?

maybe you can run that software inside wine for linux, lookup wine in google.

---

### Post by disturbedite on 2009-04-24
> **compiledkernel said:**
> Does not GFceu provide the same functionality that Nestopia does? 

It is in the repos and on g-a-i.

nestopia is the most accurate NES emulator there is.

i filed a bug a long time ago, but nobody has packaged it.

as for instructions, for compiling, they can be found in the last two posts here:
[https://bugs.launchpad.net/ubuntu/+bug/178034](https://bugs.launchpad.net/ubuntu/+bug/178034)

i switched to opensuse a while back and nestopia is packaged for opensuse, so i don't have to compile it. :)

---

### Post by stayfly on 2009-04-24
> **compiledkernel said:**
> Does not GFceu provide the same functionality that Nestopia does? 

It is in the repos and on g-a-i.

thanks, that seems to work pretty well

edit: it works ok but Nestopia is much better in my opinion

I tried Nestopia on Wine and it's pretty good. about 90% as good as what it is in Windows XP.

I would love to get the Linux version of Nestopia working if anyone can please explain how to do it.

---

### Post by mister_playboy on 2009-08-24
Download the the source from [[COLOR="Red"]here[/COLOR]](http://sourceforge.net/projects/nestopia/files/Nestopia/v1.40/Nestopia140src.zip/download) and extract the contents into a folder... I'll call it Nestopia.

Download the Linux overlay from [[COLOR="Red"]here[/COLOR]](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip) and extract the contents into the same folder as the source.

Open the terminal, go to the location of the folder Nestopia and type:

```
make
```
for single CPU computers
```
make -j3
```
for dual-cores or
```
make -j5
```
for quad-cores.

Create a folder in your home directory called .nestopia and copy NstDatabase.xml and nstcontrols from the Nestopia folder to the new .nestopia folder.

Double click on the file nst in the Nestopia folder to run the emulator... I don't think there is any "install" functionality, so you'll have to create a launcher manually if you want to run it from Applications in your panel.

---

### Post by zer010 on 2010-07-03
I am running 10.04 trying to "make" Nestopia, and I get this msg:

~/Games/Nestopia140src$ make
Creating output directory objs
Creating output directory objs/core
Creating output directory objs/core/api
Creating output directory objs/core/board
Creating output directory objs/core/input
Creating output directory objs/core/vssystem
Creating output directory objs/linux
Creating output directory objs/linux/7zip
Creating output directory objs/linux/unzip
Creating output directory objs/nes_ntsc
Compiling source/linux/main.cpp...
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [objs/linux/main.o] Error 1

What do I need to do now?
Nestopia runs too slow under Wine.
GFEUX is NOT as good as Nestopia.

---

### Post by Perfect Storm on 2010-07-03
If you read your terminal output;
> /bin/sh: sdl-config: not found

Install libsdl (-dev) package

> No package 'gtk+-2.0' found

Install libgtk2 (-dev) package.

> gcc: error trying to exec 'cc1plus': execvp: No such file or directory

Install the meta package build-essential for getting default compiling tools.

---

### Post by zer010 on 2010-08-14
I don't know what I did to get close to compiling the ever elusive Nestopia. However, I tried to do it again, and ......Nothing! Yay! :confused: Screw it. I guess I can try GFCEUwhatever again. Last few times I could never get it to map buttons. It just ...did not work.  It is just so inferior to Nestopia....

---

### Post by disturbedite on 2010-08-14
> **zer010 said:**
> I don't know what I did to get close to compiling the ever elusive Nestopia. However, I tried to do it again, and ......Nothing! Yay! :confused: Screw it. I guess I can try GFCEUwhatever again. Last few times I could never get it to map buttons. It just ...did not work.  It is just so inferior to Nestopia....
it sounds like you're not doing it right which is why you can't compile it. the instructions are right at the bottom of the linux home page: [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200)

---

### Post by beloved88 on 2010-08-21
Hey.  I really want to learn how to compile my own software, but i'm running across a few things.  I've installed both the libsdl-dev and libgtk2.0-dev packages before compiling, then ran make -j3 (since i'm running a hyperthreaded atom processor) and things seemed to go well, until i tried to run it, and nothing happens.  I opened a CLI and ran ./nst from the folder i compiled it in, and got this:
```
beloved88@Skipper:~/Nestopia$ ./nst
Couldn't read ~/.nestopia/nstcontrols file
```
do i need to create and/or edit this file?

---

### Post by beloved88 on 2010-08-21
> **mister_playboy said:**
> Create a folder in your home directory called .nestopia and copy NstDatabase.xml and nstcontrols from the Nestopia folder to the new .nestopia folder.

Double click on the file nst in the Nestopia folder to run the emulator... I don't think there is any "install" functionality, so you'll have to create a launcher manually if you want to run it from Applications in your panel.

sorry, didn't read that part.  You're right, i never really thought about the difference between the words "compile" and "install"

---

### Post by beloved88 on 2010-08-21
It works great.  Much better than the others i've tried.  But one thing is... curious.  It seems with about every single emulator i've tried with my computer, the perfomance isn;t nearly what i think it oughtta be.  I remember as a kid playing emulators on a box running windows 98 with a 800mhz Pentium III CPU, and i can't really think if there was a discrete GPU or not, but thinking about it, i don't think so.  It would run emulators up to ZSNES and Kega perfectly.  I figured with my current computer, a netbook running an Atom N280 clocked at 1.66 ghz +hyperthreading, my computer should run these emulator just fine, even with the intel integrated graphics.  but i've been kinda dissapointed except for ZSNES, which is the only one that will run games at full speed w no choppiness whatsoever.  The curious thing is that it also will run my CPU to 95%, while all the others only go to 50% (they will only use a single logical core... WHY!?!?!) i was really hopefully when i saw that you could specify Nestopia to build for dual core machines, but alas, it only uses 50% of my processor, and there are minor issue with visually annoying frame skips.  any idea from anyone?
Oh, i'm running Vanilla Lucid, if that helps (can't stand UNR)

---

### Post by beloved88 on 2010-08-21
posting a new thread, cause this is off topic from OP

---

