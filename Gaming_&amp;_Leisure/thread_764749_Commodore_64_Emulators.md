---
title: "Commodore 64 Emulators"
date: 2008-04-24
forum: Gaming &amp; Leisure
---

### Post by canadiandude007 on 2008-04-24
Hello,

I am curious as to whether anyone has compiled/installed and got working a decent Commodore 64 emulator?

I know VICE is targeted for Linux, but just wondering whether other people have used any.

You can find a list of emulators here:
[http://www.c64.cc/Emulators/](http://www.c64.cc/Emulators/) 

As well as a huge C64 repository here:
[http://www.c64.cc/](http://www.c64.cc/)
[http://www.c64.org/](http://www.c64.org/)
[http://www.c64.com/](http://www.c64.com/)
[http://www.lemon64.com/](http://www.lemon64.com/)

Tons of Commodore 64 games, apps, etc out there.

Cheers!

---

### Post by Wobedraggled on 2008-04-24
Vice just works, so I go with that.

---

### Post by Grishka on 2008-04-24
there are a few C64 emulators for Linux, but VICE is the best, perhaps even better than CCS64 (an old DOS/Windows emulator). other emulators seem dated and incomplete in comparison. VICE has got a nice GUI, can be easily configured and tweaked to your liking, and emulates C128 just as well.
oh, and it's in the repos, so no compiling is necessary.

---

### Post by k33bz on 2008-05-02
my only problem with vice, is that my screen stays black, i cant see a damn thing. although i have not seriously worked on it to see what the problem is. but will do so one of these days. I use to love vice when i had it on windows.

---

### Post by linuxlizard on 2008-05-02
another vote for vice. I haven't used it in a couple releases though because it wants the rom files and I have no idea where to paste them.

One thing about vice that bugs me in windows and linux is full screen mode. windows never does it right- either leaves black borders around the full screen picture or part of the emulated picture ends up chopped off. Linux I've never even been able to get full screen mode to work- only a window.

---

### Post by Grishka on 2008-05-02
> **linuxlizard said:**
> another vote for vice. I haven't used it in a couple releases though because it wants the rom files and I have no idea where to paste them.

One thing about vice that bugs me in windows and linux is full screen mode. windows never does it right- either leaves black borders around the full screen picture or part of the emulated picture ends up chopped off. Linux I've never even been able to get full screen mode to work- only a window.

that's odd, but it seems that ROMs are included in the Ubuntu package, even though synaptic states otherwise.
as for the fullscreen mode, it's tricky to get it working well. I recall getting a working fullscreen mode in the past, but I think I've compiled VICE from source then. fullscreen mode in VICE from the repos won't work well on my system as well.

---

### Post by UncleMonty on 2009-05-14
> **Grishka said:**
> that's odd, but it seems that ROMs are included in the Ubuntu package, even though synaptic states otherwise.
as for the fullscreen mode, it's tricky to get it working well. I recall getting a working fullscreen mode in the past, but I think I've compiled VICE from source then. fullscreen mode in VICE from the repos won't work well on my system as well.


Is it possible to expand the box or make it full screen now? It's really far too small to play the games at the moment.

---

### Post by Grishka on 2009-05-15
> **UncleMonty said:**
> Is it possible to expand the box or make it full screen now? It's really far too small to play the games at the moment.

yes, it's quite capable of stretching the view to any resolution, and going fullscreen. just turn on hardware scaling in vic settings.

---

### Post by u235sentinel on 2009-05-15
> **k33bz said:**
> my only problem with vice, is that my screen stays black, i cant see a damn thing. although i have not seriously worked on it to see what the problem is. but will do so one of these days. I use to love vice when i had it on windows.

I haven't had a problem with it.  Not sure why you would have that problem.  Driver issues?

---

### Post by awe on 2009-09-30
I am sorry to disagree with most of you. VICE works OK but has some annoying bug with the menus for disk drives. Options come on and off simply by having the mouse pointer on them. The best environment for cross-assembling and debugging that I have used so far is Windows+VICE+Relaunch64. With this setup you just type your code, press an "F" key (I think it was F5), and then VICE opens and runs your program automatically. I am very disappointed that nothing on Linux comes close to that. Meanwhile, with Ubuntu I'm still given the old VICE 1.22, while current release is 2.1. On the VICE webpage you can download binaries for so many platforms, even for the Amiga, but no DEB package. I am noy used to configuring and compiling so I have failed to compile the current VICE 2.1 on my Ubuntu.

I have not been developing for the Commodore for years because I have moved to Linux. As sad as it is, it's a fact.

---

### Post by BoyOfDestiny on 2009-09-30
That is sad. Hopefully you've at least enjoyed some SID files with audacious? 

VICE 2.1 with gnome-ui option doesn't have any strange mouse hovering issues in the GUI. 

As for auto launching things, maybe I misunderstood, I can load any old tape or disk image with vice and have it auto-run (i.e. right click open with vice.)

Anyway, I did compile VICE a while ago, if you want any help, just post. I'm willing to walk you through each step. Once you've done it once you are set. 

I compiled it when 2.1 was released, it is still running perfectly, even though I've upgraded to the Ubuntu 9.10 alphas...

Also, ubuntu 9.10 does ship with vice 2.1
[http://packages.ubuntu.com/karmic/vice](http://packages.ubuntu.com/karmic/vice)

You can try the deb package on your current install, although it looks like it's excluding the Commodore 64 kernal and I don't know which gui toolkit it is built with...

---

### Post by awe on 2009-10-01
That is good news. I'll re-try VICE when Ubuntu 9.10 is around with VICE 2.1, although I'll miss the complete working environment I once had. Pressing F5 in Relaunch64 would compile de code and then run it, all automatically, and that was great. Last time I tried wine (I mean the software) Relaunch64 would start but was barely useable. I do not like the idea of having to type the code, then go to the terminal and type a command to compile assembler, then open VICE, load the program by hand, and then launch it. Nope! Doing all of that manually is a terrible waste of time.

---

### Post by Maheriano on 2009-10-01
I have a related question, does anyone remember this Commodore 64 game?

You're on the wall of a castle and you have to get from the left side of the screen to the right side and along the way are obstacles. First it starts off with some holes to jump over, then there are arrows going across the screen, then there are guards in the holes poking upwards and finally after a number of screens you get over to the princess. And there's a looped midi tune playing in the background that's very catchy.

---

### Post by freecounter on 2009-10-01
hmm maybe canon fodder?

---

### Post by Perfect Storm on 2009-10-01
> **Maheriano said:**
> I have a related question, does anyone remember this Commodore 64 game?

You're on the wall of a castle and you have to get from the left side of the screen to the right side and along the way are obstacles. First it starts off with some holes to jump over, then there are arrows going across the screen, then there are guards in the holes poking upwards and finally after a number of screens you get over to the princess. And there's a looped midi tune playing in the background that's very catchy.

Sounds like "Aztec Challenge"

[http://www.youtube.com/watch?v=udtsv15fWH0](http://www.youtube.com/watch?v=udtsv15fWH0)

---

### Post by Maheriano on 2009-10-02
Nope, just got the game from Google!

[http://homepages.tesco.net/~parsonsp/html/hunchback.html](http://homepages.tesco.net/~parsonsp/html/hunchback.html)

---

### Post by paulita78 on 2009-12-28
I installed with all necesary libraries but does not work,why?:(

---

### Post by paulita78 on 2010-01-23
I solved it thanks to this: [http://www.linuxquestions.org/questions/linux-software-2/c64-vice-emulator-fails-to-load-kernal-on-ubuntu-system-566043/](http://www.linuxquestions.org/questions/linux-software-2/c64-vice-emulator-fails-to-load-kernal-on-ubuntu-system-566043/)
I hope you will be helpful
greetings!!:D

---

### Post by Maheriano on 2010-01-24
I tried Vice but it didn't seem to include the firmware, it told me to go find the firmware somewhere on the internet. Any ideas where to get it?

---

### Post by paulita78 on 2010-01-26
Hi Maheriano!Try here:
[http://www.zimmers.net/anonftp/pub/cbm/firmware/computers/c64/](http://www.zimmers.net/anonftp/pub/cbm/firmware/computers/c64/)
or here:
[http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/index.html](http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/index.html)
I'm very novice,anyway, in the previous post I included a link where they explain very well how to operate vice.In my case I did the following: Download from here: [http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/](http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/) this package:vice-2.2.tar.gz VICE 2.2 source code.Then pulled out the folder data.In my personal folder I created a directory called. vice, and inside I copied the contents of the folder data.And vice works perfect!I hope you will be helpful[]("http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/vice-2.2.tar.gz")[IMG]http://www.google.es/images/cleardot.gif[/IMG]

---

### Post by avw1 on 2010-03-26
> **Maheriano said:**
> I have a related question, does anyone remember this Commodore 64 game?

You're on the wall of a castle and you have to get from the left side of the screen to the right side and along the way are obstacles. First it starts off with some holes to jump over, then there are arrows going across the screen, then there are guards in the holes poking upwards and finally after a number of screens you get over to the princess. And there's a looped midi tune playing in the background that's very catchy.

i Think the game you are referring to is hunchback.

---

### Post by zoomy942 on 2010-03-28
anyone ever play robinsons reqiuem?

---

### Post by afrodeity on 2011-01-31
check out [http://frodo.cebix.net/](http://frodo.cebix.net/)

anyone know how to load a programme?

syntax example given is:

LOAD"<name>",8,1 and started with SYS49152

but if I try this I get:

LOAD }PROGRAMME} ,8,1

so not sure if i am pressing wrong key, 

I can get < > but not " "

---

### Post by mips on 2011-02-01
> **afrodeity said:**
> check out [http://frodo.cebix.net/](http://frodo.cebix.net/)

anyone know how to load a programme?

syntax example given is:

LOAD"<name>",8,1 and started with SYS49152

but if I try this I get:

LOAD }PROGRAMME} ,8,1

so not sure if i am pressing wrong key, 

I can get < > but not " "

It probably uses original c64 keyboard emulation/layout so the key mappings won't be standard.

To get " type SHIFT+2

So LOAD "filename" ,8,1


[IMG]http://www.classiccmp.org/dunfield/c64/h/front.jpg[/IMG]
Will probably have to do a google search to get correct key mappings.

---

### Post by afrodeity on 2011-02-02
thanks I found it :) love the pic

---

### Post by MethosCR on 2011-02-11
I'm gonna install VICE but my old Commodore 64 still works! :lolflag:

I'm gonna take a pic to post it here. :o

---

### Post by afrodeity on 2011-02-12
Found an old C64 minus power supply, cartridge or cables in a second hand store this week!!!

---

