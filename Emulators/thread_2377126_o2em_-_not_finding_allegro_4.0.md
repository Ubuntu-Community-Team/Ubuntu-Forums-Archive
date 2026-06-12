---
title: "o2em - not finding allegro 4.0"
date: 2017-11-09
forum: Emulators
---

### Post by michael337 on 2017-11-09
I have o2em, and even though I've installed liballegro4.4, it still gives me a message saying:
> error while loading shared libraries: liballeg.so.4.0: cannot open shared object file: No such file or directory
I cannot find allegro 4.0 on launchpad, and I can't even manually do it because I don't have my environment table for djgpp. I've never heard of it, and this is starting to feel pointless, because I just wanted to play a stupid game in the first place, not going deeper and deeper finding packages. Is therean easier solution to this?

---

### Post by adec2 on 2017-11-10
[COLOR=#0000FF][FONT=&amp]sudo apt install liballegro4.4 from terminal[/FONT][/COLOR]

---

### Post by kostkon on 2017-11-10
I downloaded the zip file from [its website]("http://o2em.sourceforge.net/") and, wow it's from 2004! Well, first of all, I'm pretty sure the binary is 32bit. Also, I'll assume here that you are on a 64bit installation. So, you could try installing the 32bit version of liballegro4.4 with:
```
sudo apt-get install liballegro4.4:i386
```
Since library packages have been made multiarch, the 32bit version of liballeg.so.4.4 resides in /usr/lib/i386-linux-gnu/allegro/  instead of where, I'm assuming, o2em is looking for the file anyway, that is, in /usr/lib/allegro/.

Here's an idea: you could try creating a soft link named /usr/lib/allegro/liballeg.so.4.0 that will point to /usr/lib/i386-linux-gnu/allegro/liballeg.so.4.4 or something along those lines. You might, also, need to do the same for the rest of the allegro library files.

Hope that helps somehow.

---

### Post by michael337 on 2017-11-19
Thank you for solving that! But a new problem popped up. It says > undefined symbol: _accel_driver


>:(

---

### Post by michael337 on 2017-11-26
BUMP. There has to be some kind of solution!

---

### Post by Holger_Gehrke on 2017-11-26
The easy solution is to not use o2em; M.A.M.E. (Multi Arcade Machine Emulator) and MESS (Multi Emulator Super System) are one project since 2015 and the MAME binaries in the repositories should contain everything needed to emulate the Odyssey 2 and its variants. Although I have to admit that getting MAME or MESS to do exactly what you want is another rabbit hole down which one can vanish ... :biggrin:

Holger

---

### Post by michael337 on 2017-12-08
> **Holger_Gehrke said:**
> The easy solution is to not use o2em; M.A.M.E. (Multi Arcade Machine Emulator) and MESS (Multi Emulator Super System) are one project since 2015 and the MAME binaries in the repositories should contain everything needed to emulate the Odyssey 2 and its variants. Although I have to admit that getting MAME or MESS to do exactly what you want is another rabbit hole down which one can vanish ... :biggrin:

Holger
The problem is is that I’ve tried to use Mame, but when I load the game ‘trans american rally’, it doesn’t load properly, and I see four zeroes on the top. Am I using the wrong system? Because it’s a videopac plus game.

---

### Post by Holger_Gehrke on 2017-12-10
There is a separate core for those, named "Videopac Plus G7400" in the menu. As I don't have that game or any other games that need this, I can't tell you whether it is any good, but the status display of mame says "Overall: working  Graphics Imperfect, Sound OK".

Holger

---

