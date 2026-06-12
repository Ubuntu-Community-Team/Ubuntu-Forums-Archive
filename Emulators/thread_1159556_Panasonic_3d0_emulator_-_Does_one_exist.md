---
title: "Panasonic 3d0 emulator - Does one exist?"
date: 2009-05-14
forum: Emulators
---

### Post by QwUo173Hy on 2009-05-14
I can't seem to find an emulator for this platform. Admittedly the titles weren't great, but there was one masterpiece : Road Rash, that I have and would love to be able to play.

---

### Post by CharmyBee on 2009-05-14
The best (and only playable) one that exists is this one:

[http://www.freedo.org/](http://www.freedo.org/)

It's for Windows only though and it's been inactive for 2 years. There are none for Linux.

Be sure to have a beefy (2.2ghz+) machine for this one.

Alternatively there's the old rare [Creative 3DO Blaster](http://en.wikipedia.org/wiki/3DO_Blaster) ISA card which was a 3DO itself you could mount in your computer. It won't work of course, you'll have to build an old computer to use that one. It's not emulation.

> **jarlath said:**
> masterpiece : Road Rash

Oh yes the 3DO version was the best!

---

### Post by QwUo173Hy on 2009-05-14
Fair play to ya CharmyBee - what are the chances of someone so knowledgable being on the baords! There is nothing on the 3D0 on this forum till now. I'll definitely try out those options. 

I did find this [project]("http://www.aep-emu.de/Emus-file-emus_x-id-39-system-Linux.html") but it's in another language and no doubt involves compilation with outdated libraries etc.

Thanks a million for your help, I'll let you know if I get it going. Do you still have a 3D0 yourself? I'm half thinking of buying one on eBay or something.

---

### Post by CharmyBee on 2009-05-14
> **jarlath said:**
> I'll let you know if I get it going. Do you still have a 3D0 yourself? 

i've never had one, played one _at_ school in the mid '90s though (back when urban public schools were an 'anything goes' kind of place)

It also helps to search for 3D**O** rather than 3D**0**.

MESS isn't a dedicated emulator for 3DO though. Its goal is to emulate everything.

---

### Post by QwUo173Hy on 2009-05-14
Okay, wow - that's a pretty ambitious goal. I'm going to try to get freedo working on wine. Long shot but not a difficult shot.

---

### Post by prylux on 2010-07-25
FreeDO is the only one I've found so far.

 I am using Ubuntu 10.04 on a Laptop with Intel Pentium Dual Core processor T2330 at 1.6GHz, 4GB of DDR2 memory, a 120GB hard drive and Intel Graphics Media Accelerator X3100 graphics.

I'm running FreeDO Beta 1.8 using Cross Over Pro 8 (to make wine simple). I can play most games, some (The Hord) have color problems
most have some texture tearing but not usually enough to ruin a game. I also have sound issues where the sound seems to be running out of buffer space (there are pauses in the sound) but they are playable. I could be having these issues because of my hardware but that FreeDO will play the games at full speed with no slowdown on what I consider low specs is a good sign.

I have personally tested as playable:
GEX
Star Control II
Road Rash
Need for Speed, The (did crash on me once though)
Battle Chess
Flashback

Unplayable (On my system anyway)
Wing Commander III - Heart of the Tiger (Wrong colors and crashes)
Hord, The (I could play it but it looks like your playing at night)

Also thought I should mention it runs better in fullscreen than in a window

---

### Post by QwUo173Hy on 2010-07-26
Prylux, thanks for that. New motivation to get my Road Rash working again ;)

---

### Post by honeybear on 2012-02-03
you can play your cdrom with xmess using the 3do.c driver

[http://www.mess.org/mess:drivers:3do:3do](http://www.mess.org/mess:drivers:3do:3do)

---

### Post by QwUo173Hy on 2012-02-03
> **honeybear said:**
> you can play your cdrom with xmess using the 3do.c driver

[http://www.mess.org/mess:drivers:3do:3do](http://www.mess.org/mess:drivers:3do:3do)

Thanks honeybear, I'll try that and see how it goes.

---

### Post by honeybear on 2012-02-03
> **jarlath said:**
> Thanks honeybear, I'll try that and see how it goes.

you can also find freedo for linux as source 
[http://www.dcemu.co.uk/vbulletin/threads/118098-freedo-is-Going-OpenSource-3D0-Emulator](http://www.dcemu.co.uk/vbulletin/threads/118098-freedo-is-Going-OpenSource-3D0-Emulator)

---

### Post by honeybear on 2012-02-04
so you must get sdlmess, and then 
[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

follow this command:
 
```
 xterm -e sdlmess -biospath ~/bioss/  edo  -fullscreen -s 2  -jt 5 -cart  /tmp/gamefolder/game.iso
``` 
make sure that the /tmp/gamefolder/ is fully given.


or if it still works: 

> sudo su
echo deb [http://apt.ludomatic.fr](http://apt.ludomatic.fr) lenny non-free >> /etc/apt/sources.list.d/ludomatic.list
echo deb-src [http://apt.ludomatic.fr](http://apt.ludomatic.fr) lenny non-free  >> /etc/apt/sources.list.d/ludomatic.list
wget [http://apt.ludomatic.fr/ludomatic.key.asc](http://apt.ludomatic.fr/ludomatic.key.asc) -O - | apt-key add -
apt-get update
apt-get install sdlmame sdlmess
exit
@ address: [http://apt.ludomatic.fr/pool/non-free/s/sdlmess/](http://apt.ludomatic.fr/pool/non-free/s/sdlmess/)

---

### Post by honeybear on 2012-03-05
hi,

If freedo works, I would be glad to test it. 

Could you please an howto or ideally a bash script that installs it and run it for a given free game or any other alternative? 

So after downloaded it, how have you managed to run it? 

Does it work with the famous 3do battle chess game?

---

### Post by honeybear on 2012-03-12
2011 news, of freedo, it looks still active.

however, if you look into: [http://www.freedo.org/HTML/downloads.html](http://www.freedo.org/HTML/downloads.html)

you find only EXE files, so no sources tar.gz or ./ executable for linux


--edit
or maybe here: [http://www.arts-union.ru/node/75](http://www.arts-union.ru/node/75)

---

### Post by honeybear on 2012-03-12
OK... got it to work: 

To run 3do for LINUX, you could type the following: 
1/ 
> sudo  apt-get install  libqt4-opengl


2/
```

#!/bin/sh
cd 
mkdir tmp 
cd tmp 

wget -N http://www.arts-union.ru/sites/default/files/FreeDO21qt_linux.zip

unzip FreeDO21qt_linux.zip

ls

./FreeDO 


```


Then no idea how it works. 

It gives this screenshot.

---

### Post by honeybear on 2013-03-06
Hi

I just tried under downlaods.... but there is only the EXE for windows and no source files. 

[http://www.freedo.org/](http://www.freedo.org/)

Does Ubuntu develop a bit in that direction to add one emu to our repos?

rgds

---

### Post by QwUo173Hy on 2013-03-08
I haven't got this working - in fact, I forgot about it. It was tricky getting it to work (it didn't) and it looked hopeless. But I may try again soon and get back to you. Unless the performance is great though this doesn't really interest me.

---

### Post by QwUo173Hy on 2013-05-25
Sorry for waking the dead, but I finally got this working using:
Ubuntu 13.04 with Graphics Accelleration
Wine
FreeDo 1.9

Happy days.

---

### Post by matt_symes on 2013-05-25
I'm glad you got it working :D

However, as this is such an old thread, I'll close it.

---

