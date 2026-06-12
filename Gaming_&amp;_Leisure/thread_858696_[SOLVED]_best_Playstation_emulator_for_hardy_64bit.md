---
title: "[SOLVED] best Playstation emulator for hardy 64bit?"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by tjwoosta on 2008-07-13
so ive been thinking of installing a playstation emulator


i found a couple that say they are compatible with linux, and of course each one says there emulator is the best

so i figure i should ask the guys who know

which playstation emulator shoud i get for hardy 64bit?


EDIT: also while im making this post i might as well ask is there any way to make Mupen64 work on hardy 64bit?

or does anybody know of any other n64 emulator that will work?

---

### Post by Sockerdrickan on 2008-07-14
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

mupen64plus is native 64bit

---

### Post by acoustibop on 2008-07-14
See dfreer's thread [How-To: install pSX on AMD64/i386]("http://ubuntuforums.org/showthread.php?t=394097"), tjwoosta.

---

### Post by tjwoosta on 2008-07-14
> See dfreer's thread How-To: install pSX on AMD64/i386, tjwoosta. 

i tried installing from that thread but they only give the gutsy repository

then i tried just adding it anyway, but when i do apt-get update it fails to load that site


EDIT:  ok i used the OLD install method mentioned and it seems to work great 

(i got it to start and i get the main playstation welcome screen that says music cd and memory card, but i havnt tested it with a game yet)

ill post back if it works

---

### Post by tjwoosta on 2008-07-14
awesome, it works

thank you guys for your help

i got everything working perfectly  (including my gamepad)

---

### Post by tjwoosta on 2008-07-14
tuxor, in your signature i noticed the gamecube emulator


should that work on hardy 64bit?

i tried compiling but when i run make i get this error
> 
tj@tj-laptop:~/tuxcube/source$ make
In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:21:31: error: SDL/SDL_byteorder.h: No such file or directory
make: *** [ppc_disasm.o] Error 1
tj@tj-laptop:~/tuxcube/source$ 


do you know what am i doing wrong?

EDIT: i fixed it, im stupid and forgot to install the dependencies

it works great now (for what it is anyway)

---

### Post by gps.fanatic on 2008-07-16
@tjwoosta
I have tried tuxcube and I got the same problem.
I have Ubuntu 8.04 64-bit.

---

### Post by tjwoosta on 2008-07-16
> 
@tjwoosta
I have tried tuxcube and I got the same problem.
I have Ubuntu 8.04 64-bit. 

ahh.. yea sorry i forgot to mention where i found the dependencies that i needed


well this is the thread that i ended up following
> 
[http://ubuntuforums.org/showthread.php?t=620851&highlight=tuxcube](http://ubuntuforums.org/showthread.php?t=620851&highlight=tuxcube)

just install the libs that are mentioned in the first post

then just compile like normal

---

### Post by whyzee7 on 2008-07-28
guys i'm new to ubuntu. i,ve donloded turball and extracted it only to find a psx folder. the sudo apt command on dfreer's thread in the terminal gave the msg as "couldn't find package psx". please help. also i dont know 32 or 64 bit thing. what is i386 BTW. please do reply as soon as possible

---

### Post by tjwoosta on 2008-07-28
well first off we would need to know are you using 32bit ubuntu or 64bit?

if you are unsure as to what version you are running just put this command int he terminal

```
uname -a
```

it should give you something that looks like this

```

Linux tj-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 **x86_64** GNU/Linux

```

in my case it says x86_64 wich i know is 64bit ubuntu

if you have 32bit it will say either i386 or i686

now depending on weather you have 32bit or 64bit you will need different dependencies


I think the install insructions mentioned at the top of dfreer's thread might be outdated  (wich would explain why it wont work for you)

but if you are using 64bit you can simply follow the **OLD** instructions mentioned at the bottom of the first post in dfreer's thread


if you have 32bit then i really dont have any idea what dependencies you would need to compile (since i never had to do it) but you should be able to just download the package from the pSX website and compile it yourself
[http://psxemulator.gazaxian.com/]("http://psxemulator.gazaxian.com/")

to compile anything the first thing you would ever need is build-essential
```
sudo apt-get install build-essential
```

then just extract your .tar.gz to wherever you want  (right click it and choose extract)

then navigate to the newly extracted directory and read the readme file thats included  (it should tell you exactly what commands to use to install and what dependncies you will need, if any)

but when you run the commands to install, make sure that you cd to the pSX directory first

```
cd wherever/you/extracted/the/files
```

then just run the install commands from there  

usually it will be like this

```
./configure
```
then
```
make
```
then
```
sudo make install
```

---

### Post by acoustibop on 2008-07-29
You don't need to compile anything for pSX.  For a standard Ubuntu 32bit installation, just install libgtkglext1 (in the repositories) and you should be good to go.  For 64bit, you may need to force the install of some 32bit libraries - see dfreer's thread.

pSX is closed source and only comes as a pre-compiled binary.  If you have the necessary dependencies installed, all you do is un-tar it and run it.

You will, of course, need a Playstation BIOS, a working 3D videocard and a working soundcard - and games.

---

