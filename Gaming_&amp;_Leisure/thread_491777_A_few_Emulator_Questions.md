---
title: "A few Emulator Questions"
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by Nythain on 2007-07-04
A. Are there any decent Gameboy Advance emulators that support cheating (eg. Codebreaker or GameGenie codes, or with a Search feature similar to VisualBoyAdvance for windows)

B. Has anyone gotten csnes9x (a command line front end for snes9x) to install on ubuntu feisty... i try but get a bunch of errors, the first few being expected constructor, destructor, or type conversion before <... i have no idea what a constructor/destructor/type conversion are since im not a programmer...

C. well actually thats it, just a and b there... thanks

---

### Post by marq on 2007-07-05
for b, have u tried zsnes instead, works alot better in my opinion

downlaod the source files from [http://www.zsnes.com]("http://www.zsnes.com")

extract it to ur home folder

in the terminal do -> sudo apt-get install libsdl1.2-dev libpng12-dev nasm zlib1g-dev

then in the terminal write cd and drag ur new folder called src into the terminal (found at home/zsnes_1_51)

then ./configure
make
sudo make install

and it should work
run with zsnes in the terminal or press alt+f2 and write zsnes

---

### Post by hikaricore on 2007-07-05
GetDeb.net has an up-to-date zsnes package: [http://www.getdeb.net/app.php?name=ZSNES](http://www.getdeb.net/app.php?name=ZSNES)

(not sure if you're interested in it or not since you were obviously asking about snes9x)

---

### Post by Nythain on 2007-07-05
i havent looked to into it yet... does it have an interactive interface, or is it strictly called upon by lengthy syntax commands... the only reason i wasked about csnes9x was the fact that its a curses front end... while i love the command line, im still a little lazy and prefer not to have to type the longest commands known to man... not to mention that FINDING a certain rom on my computer and typing its name out is complicated enough... but i will definately check it out

---

### Post by Nythain on 2007-07-05
frickin sweet, a simple zsnes command and its that oh so familiar interface... exactly the same as teh windows equivalent... thanks for the info guys

---

### Post by BoyOfDestiny on 2007-07-14
> **Nythain said:**
> A. Are there any decent Gameboy Advance emulators that support cheating (eg. Codebreaker or GameGenie codes, or with a Search feature similar to VisualBoyAdvance for windows)

B. Has anyone gotten csnes9x (a command line front end for snes9x) to install on ubuntu feisty... i try but get a bunch of errors, the first few being expected constructor, destructor, or type conversion before <... i have no idea what a constructor/destructor/type conversion are since im not a programmer...

C. well actually thats it, just a and b there... thanks

A. Mednafen handles 'Atari Lynx, GameBoy (Color), GameBoy Advance, NES, PC Engine(TurboGrafx 16), SuperGrafx, Neo Geo Pocket (Color), PC-FX, and WonderSwan (Color)'. It has a nice cheat interface too. Handles Codebreaker codes for GBA. 

[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

Anyway, I'm used to the zsnes cheat search, this isn't too much different. You just use
alt + c to enter the cheat interface
alt + t toggles cheats on/off during gameplay

Hope this is what you're looking for.

---

### Post by yanom on 2009-05-27
> **BoyOfDestiny said:**
> A. Mednafen handles 'Atari Lynx, GameBoy (Color), GameBoy Advance, NES, PC Engine(TurboGrafx 16), SuperGrafx, Neo Geo Pocket (Color), PC-FX, and WonderSwan (Color)'. It has a nice cheat interface too. Handles Codebreaker codes for GBA. 

[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

Anyway, I'm used to the zsnes cheat search, this isn't too much different. You just use
alt + c to enter the cheat interface
alt + t toggles cheats on/off during gameplay

Hope this is what you're looking for.

I can't seem to find the place to add codebreaker code for GBA. just regular memory cheat.

---

### Post by disturbedite on 2009-05-28
for snes emulation, BSNES is the hands-down best (most accurate) SNES emulator in existence, if your system can handle the system requirements that is.

---

### Post by CharmyBee on 2009-05-28
> **disturbedite said:**
> for snes emulation, BSNES is the hands-down best (most accurate) SNES emulator in existence, if your system can handle the system requirements that is.

While accurate, it currently can't hold the 'best' title as it doesn't emulate the addon chips in certain cartridges yet.

---

### Post by disturbedite on 2009-05-28
> **CharmyBee said:**
> While accurate, it currently can't hold the 'best' title as it doesn't emulate the addon chips in certain cartridges yet.

true. however, very few carts use those. i, as well as most think that its accuracy outweighs the lack of emulation of those special chips and makes it the best.

---

### Post by Sef on 2009-05-28
Locked for necromancy.

---

