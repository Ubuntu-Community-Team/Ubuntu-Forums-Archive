---
title: "Mednafen"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by nofx135 on 2007-08-08
how do i start or run Mednafen, i just intalled it through a deb file, im running on fiesty fawn

ohh and for some reason when im in the terminal and i need to type my password(my password contains all #) it doesnt let me type any # , ive tried toggling num lock 

can someone pleaz help me

---

### Post by nofx135 on 2007-08-08
also in znes, for some reason it aint loading my game save for earthbound, it will load the rom but doesnt load the save ( the save is a .srm file)

can anyone help, cuz i dont wanna have to start a new game

---

### Post by nofx135 on 2007-08-08
i solved the terminal password problem but still need help /w  Mednafen ( how to start it or run it) and the zsnes game save

---

### Post by BoyOfDestiny on 2007-08-08
> **nofx135 said:**
> i solved the terminal password problem but still need help /w  Mednafen ( how to start it or run it) and the zsnes game save

Great choices I must say (both in emulators and game)

For mednafen (from terminal), 
mednafen nameofgame

I suggest just right clicking your rom and doing an "open with", (pick mednafen from the list, if not; custom command) 
mednafen

It should remember.

Also, not sure what version of mednafen you have (I'm running 0.8.3 beta), make sure to press F1 to learn the key bindings to change for keyboard/gamepad, rewind, save state, etc...

As for your earthbound zsnes save, make sure the filename matches the save game name.

i.e. earthbound.smc, the save file should be earthbound.srm
and it should be located in your home folder under .zsnes folder
(for hidden files in nautilus, ctrl + h)

---

### Post by nofx135 on 2007-08-08
> **BoyOfDestiny said:**
> Great choices I must say (both in emulators and game)

For mednafen (from terminal), 
mednafen nameofgame

I suggest just right clicking your rom and doing an "open with", (pick mednafen from the list, if not; custom command) 
mednafen

It should remember.

Also, not sure what version of mednafen you have (I'm running 0.8.3 beta), make sure to press F1 to learn the key bindings to change for keyboard/gamepad, rewind, save state, etc...

As for your earthbound zsnes save, make sure the filename matches the save game name.

i.e. earthbound.smc, the save file should be earthbound.srm
and it should be located in your home folder under .zsnes folder
(for hidden files in nautilus, ctrl + h)


thanx the zsnes worked, i can now load my game save
but i cant get mednafen to start, itried to type in mednafen nameofgame
like u told me to but it gave me an error : 

jd@Comp:~$ mednafen nameofgame
Starting Mednafen 0.6.5
 Loading settings from "/home/jd/.mednafen/mednafen.cfg"...
 Initializing joysticks...
 Loading nameofgame...

Error opening "nameofgame": No such file or directory
jd@Comp:~$ 

ohh and by the way im trying to run gba and nes roms and the version i installed is 0.8.1, i got the deb file from [http://ftp.debian.org/debian/pool/main/m/mednafen/](http://ftp.debian.org/debian/pool/main/m/mednafen/)
i downloaded the file called mednafen_0.8.1-1_i386.deb on the list

---

### Post by BoyOfDestiny on 2007-08-08
> **nofx135 said:**
> thanx the zsnes worked, i can now load my game save
but i cant get mednafen to start, itried to type in mednafen nameofgame
like u told me to but it gave me an error : 

jd@Comp:~$ mednafen nameofgame
Starting Mednafen 0.6.5
 Loading settings from "/home/jd/.mednafen/mednafen.cfg"...
 Initializing joysticks...
 Loading nameofgame...

Error opening "nameofgame": No such file or directory
jd@Comp:~$ 

ohh and by the way im trying to run gba and nes roms and the version i installed is 0.8.1, i got the deb file from [http://ftp.debian.org/debian/pool/main/m/mednafen/](http://ftp.debian.org/debian/pool/main/m/mednafen/)
i downloaded the file called mednafen_0.8.1-1_i386.deb on the list

By nameofgame I meant the name of game. 

mednafen your_rom.nes
mednafen your_other_rom.gba

(just replace with the name of your rom)

However, that will only work if the game is in the same folder

so something like
mednafen ~/Games/nameofrom.nes
(substitute the location of the game, Games are where mine are)

Or the right click "Open With" from nautilus, choose mednafen (or click custom command, type mednafen.)

From there you should be set to play. Like in my previous post, F1 for help

---

### Post by nofx135 on 2007-08-08
oh.....right

---

### Post by nofx135 on 2007-08-08
oh yeah works like a charm
thanx

---

### Post by BoyOfDestiny on 2007-08-08
> **nofx135 said:**
> oh yeah works like a charm
thanx

No problem. :)

---

