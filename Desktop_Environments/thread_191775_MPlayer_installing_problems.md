---
title: "MPlayer installing problems"
date: 2006-06-08
forum: Desktop Environments
---

### Post by feardotcom on 2006-06-08
Hi, im new to ubuntu, and i tried comiling mplayer, and it gave me the following errors, can someone please tell me what this means?

Checking for host cc ... cc
./configure: line 686: cc: command not found
Checking for CPU vendor ... GenuineIntel (15:3:4)
Checking for CPU type ...  Intel(R) Pentium(R) 4 CPU 3.00GHz
Checking for GCC & CPU optimization abilities ... Your cc does not even support "i386" for '-march' and '-mcpu'.
error
Checking for kernel support of mmx ... failed
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmx2 ... failed
It seems that your kernel does not correctly support mmx2.
To use mmx2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... no
Checking for assembler (as ) ... failed
Upgrade binutils to 2.9.1 ...

i was on suse, but i suse comes with so much bullshit, that you can install anything because a lib is missing and when youg o get that lib that lib is missing a lib and thent hat lib is missing a lib, and then that lib is missing a lib and when you finally get that lib up, you have to go throught he hole process again for 10 more, and i even ran into probems of not bening able to instal library files becuase of other library files that would interfere with that one. but anyway, if mplayer wont install on ubuntu do you know of a program that will run on ubuntu that has support for allt he video codecs?

---

### Post by kariopto on 2006-06-08
If you're running dapper.. just add multiverse to your sources and then run 
sudo apt-get update
sudo apt-get install mplayer

---

### Post by feardotcom on 2006-06-10
dude, thanks, that worked, i got to researching and now i can even rip dvds with k9copy, although i still cant play dvds, and mplayer always pops up a error about xv

---

### Post by mgmiller on 2006-06-10
My mplayer install did the same thing, what I did to fix it was right click on the control part of the player to get the menus and select preferences.  Go to the Video tab and try different drivers till one works without the error.  For me the default on install was on x11 and I had to change it to xv.  Click OK, then exit and restart mplayer.

---

### Post by mgmiller on 2006-06-10
As far as playing dvd's goes, you need to install package libdvdcss2.  There are a few different sources for this package that you can add to your repositories list, one is for the penguin liberation front and the other is from nerim.net.  If you use the nerim repo, disable it after getting the package, it contains many other files that could create havoc on an ubuntu system.

---

### Post by TOPPEL on 2006-06-10
[QUOTE=mgmiller]As far as playing dvd's goes, you need to install package libdvdcss2.  There are a few different sources for this package that you can add to your repositories list, one is for the penguin liberation front and the other is from nerim.net.  If you use the nerim repo, disable it after getting the package, it contains many other files that could create havoc on an ubuntu system.[/QUOTE]
from what i hear from the people that herd on freenode #ubuntu there is much more to configuring mplayer than a apt-get install.

---

