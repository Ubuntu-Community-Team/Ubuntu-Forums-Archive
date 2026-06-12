---
title: "looking for emulators (all of them)"
date: 2008-07-16
forum: Gaming &amp; Leisure
---

### Post by tjwoosta on 2008-07-16
im trying to make my laptop into the ultimate portable linux gaming console (native Linux games, WINE, and all availible Emulators)


so far i have pSX, Mupen64Plus, TuxCube, PCSX2, and snes9express

all of those seem to do exacty what i wanted (aside from tuxcube and PCSX2 but those are still in developement anyway)

so now i need to finish it off with more emulators

what other emualtors should i get?

i mean for like dreamcast, genesis, GBA, Mame, all of them


EDIT: also i forgot to mention that i am using Ubuntu Hardy 64bit

---

### Post by grossaffe on 2008-07-16
I would replace snes9express with the GTK port of SNES9x.

---

### Post by acoustibop on 2008-07-16
You could try [Mednafen]("http://mednafen.sourceforge.net/"), tjwoosta - it emulates a number of platforms, including the NES and Sega Master System - the only emulator I've found for Linux that emulates SMS satisfactorily.

It's command line-only, but I don't find this a problem; just click on a game it can play and it opens the game automatically.

Best place to get it is the [CinnamonPirate]("http://repository.cinnamonpirate.com/") repository; they generally have the most up-to-date version.  It may also be in the Ubuntu repositories, but I think that's an old pre-SMS version.

---

### Post by tjwoosta on 2008-07-16
> I would replace snes9express with the GTK port of SNES9x.

why?

i have had no troubles with snes9express at all  (and i have over 100 games)

if it aint broke dont fix it right?

> You could try Mednafen, tjwoosta

thanks, i might give it a try, but i would really prefer a GUI  

so if anybody knows of any emulators that will play genesis and/or master system that has a GUI, it would be much appreciated

also im still looking for saturn and dreamcast and gameboy advance and mame and any others you can think of?

i have seen lxdream for dreamcast and yabause for saturn

has anybody tried either of those?

---

### Post by Steveway on 2008-07-16
Gens for Genesis (there is a .deb in one of the threads here somewhere.)
And I would advise using zsnes for snes, it seems to have better performance and it is more compatible.

---

### Post by FranMichaels on 2008-07-16
The ones I have, my personal requirement is that they are Free and/or open source licensed ;)

mednafen
dosbox
pcsx-df
sdlmame
sdlmess
zsnes
scummvm
gens
desmume
lxdream (one day the intel driver on my laptop may support it I hope...)
openmsx

If there is something missing, I recommend looking at 
[http://linuxemu.retrofaction.com/](http://linuxemu.retrofaction.com/)

---

### Post by DoktorSeven on 2008-07-16
Don't forget Vice (Commodore 8-bit computers), UAE (Amiga), Stella (Atari 2600), Daphne (laserdisk arcade games), and Yabause (Saturn).

---

### Post by grossaffe on 2008-07-17
> **tjwoosta said:**
> why?

i have had no troubles with snes9express at all  (and i have over 100 games)

if it aint broke dont fix it right?

yeah, I guess...  I just really love that port; best SNES emulator I've used.

---

### Post by tjwoosta on 2008-07-17
> yeah, I guess... I just really love that port; best SNES emulator I've used. 

ok so you guys have convinced me to switch snes emulators


where can i find this gtk port of snes9x?


EDIT: the part of my post about lxdream was removed because it was a stupid question and i figured it out right after writing it

---

### Post by grossaffe on 2008-07-17
> **tjwoosta said:**
> ok so you guys have convinced me to switch snes emulators


where can i find this gtk port of snes9x?


EDIT: the part of my post about lxdream was removed because it was a stupid question and i figured it out right after writing it

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

make sure if you're compiling it from scratch that you include openGL (and make sure that openGL is activated once you get it running.)

edit: wow, it was just updated last week.  When I installed it there wasn't a .deb option.

---

### Post by Jim! on 2008-07-17
Dgen - Sega Genesis/Megadrive Emulator.
I'll also second dosbox, works great!

---

### Post by tjwoosta on 2008-07-17
> [http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

make sure if you're compiling it from scratch that you include openGL (and make sure that openGL is activated once you get it running.)

edit: wow, it was just updated last week. When I installed it there wasn't a .deb option.


awesome, thanks

ill try it out tomorrow when i get home from work


but i have onw more question before i go to bed tonight


i just installed lxdream  (compiled from source)

all seemed to go well

but now when i try to run lxdream this is what happens
```

tj@tj-laptop:~/lxdream-0.8.3$ lxdream
01:40:40 00000000 WARN  Unable to load file 'bios/dcboot.rom': No such file or directory
01:40:40 00000000 WARN  Unable to load file 'bios/dcflash.rom': No such file or directory
01:40:40 A0000000 WARN  Not using direct rendering - this is likely to be slow
tj@tj-laptop:~/lxdream-0.8.3$ 

```

i understand the part about the bios but it wont even stay open long enough for me to use the GUI to set the bios directory

it just pops up with the GUI for lxdream in the background and another popup window on top that says 
> Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)
followed by this popup when i close the other one
> Video driver 'gtk' failed to initialize (could not connect to display?)

then everything disapears 

any ideas?

---

### Post by grossaffe on 2008-07-17
I'll have to agree with all the people saying Dosbox.

---

### Post by evets25 on 2008-07-17
i know this is an ancient debate that goes back almost a decade, but I FAR prefer zsnes over snes9x. I recommend at least trying both of them out.

---

### Post by tjwoosta on 2008-07-17
> i know this is an ancient debate that goes back almost a decade, but I FAR prefer zsnes over snes9x. I recommend at least trying both of them out.


well i was originaly going to use zsnes when i first installed ubutnu (because it was the first one that i came across in synaptic)


but i had way too many troubles with it

1. i couldnt get my joypad to work (at all)

2. i couldnt get it to play my super mario world rom hacks

3. i had no sound 

then i just swictched to snes9express and everything just worked first try

---

### Post by tjwoosta on 2008-07-17
ok   one more problem to add to the list


i have gens installed and all confiugred  (or so i thought)

i do have a valid sega cd bios installed

but when i try to play a sega cd game  (sonic cd)

it says my ram cartrige is not initialized 

(does anybody know what does that mean?)

see attached screenshot


[B]EDIT: ok i got it to work  (i just went to options and turned the "sega cd sram size" to 0)

does anybody know why this happened?[/B]

---

### Post by tjwoosta on 2008-07-17
ok so now i think i have pretty much all available emulators covered

although im still looking for  gameboy, gameboy advance, gameboy color, and nintendo DS  (hopefully with a GUI)

(let me know if you can think of more)


but right now my main problem is lxdream 

can anybody help with that?

(please see my very first post on page 2 of this thread)

---

### Post by hoagtech on 2008-07-17
Hopefully this helps to the already long list, dont worry about the copies im being lazy here:


1e - Xe multi system (Sega Genesis, SMS, GG, TG-16, NES, etc)
   [www.xe-emulator.com](www.xe-emulator.com)
2e - Snes9x 1.51 GTK (Super Nintendo)
3e - prboom (Doom)
4e - SDLMAME (Arcade, Neo-Geo)
5e - Mednafen (Gameboy Advance, Gameboy, Neogeo pocket, wonderswan)
6e - Qemu (windows)

Oh and heres an install guide for all those emulators: [http://www.fileden.com/files/2007/2/23/813212/yellowdoglinux.txt](http://www.fileden.com/files/2007/2/23/813212/yellowdoglinux.txt)

---

### Post by tjwoosta on 2008-07-17
also i just stumbled onto VBA express   

it looks awesome

has anybody here used it before?

---

### Post by grossaffe on 2008-07-17
> **tjwoosta said:**
> also i just stumbled onto VBA express   

it looks awesome

has anybody here used it before?

I haven't tried that, but have you tried Tuxboy?  It was written by Tux0r.

---

### Post by evets25 on 2008-07-17
I've used visualboy advance extensively. AFAIK, It's the standard one for gameboy emulation, and should work great. There's various GUIs and versions of it, lots of choice.

---

### Post by minisori on 2008-07-18
Here is a repo (usually updated) with some emus and utilities for roms.

Mednafen is one of the promising, it support many systems just very intensive cpu use. Probably will support more in the future. It's in those repos.

> From mednafen homepage: 
The Atari Lynx, GameBoy (Color), GameBoy Advance, NES, PC Engine(TurboGrafx 16), SuperGrafx, Neo Geo Pocket (Color), PC-FX, and WonderSwan (Color) are emulated.

mess support almost everything, but i don't know if it even works, at least i never got it working.

[http://repository.cinnamonpirate.com/](http://repository.cinnamonpirate.com/)

(Sorry if i repeat, i have not read all posts xD)

---

### Post by acoustibop on 2008-07-18
Yes, I have the CinnamonPirate repository working, as [I mentioned]("http://ubuntuforums.org/showpost.php?p=5399481&postcount=3") on the first page of the thread, minisori.

Mednafen installs and runs very nicely from it, and they generally seem to have pretty much the latest version available - unlike the Ubuntu repositories. ;)

---

### Post by minisori on 2008-07-18
See, i missed few posts :P.

I have looking around at mednafen forum, seem they working on add genesis (megadrive) support.

---

### Post by tjwoosta on 2008-07-18
thanks for the repository, but i think im gonna try to stay away from mednafen 

(according to acoustibop it is "command line only")


**i need a GUI**

(not just for me but for all my cousins and nephews who love to play theese games)

---

### Post by FranMichaels on 2008-07-18
> **tjwoosta said:**
> thanks for the repository, but i think im gonna try to stay away from mednafen 

(according to acoustibop it is "command line only")


**i need a GUI**

(not just for me but for all my cousins and nephews who love to play theese games)

I would recommend you try it. It is one of the best, IMHO, I've been using emulators since the 90's (if that makes my opinion worth more, dunno... ;) ) 

An emulator is for running the games (well, saving and cheating are nice too) it is easy to just double click your rom and have it open in mednafen. Configuring the gamepad can be done on the fly, just press F1 for in emulator hotkeys.

Anyway, if you must have GUI, here is a nice front-end 

[http://mednafenfe.sourceforge.net/](http://mednafenfe.sourceforge.net/)

Forum posts about it here
[http://ubuntuforums.org/showthread.php?t=813785](http://ubuntuforums.org/showthread.php?t=813785)

---

### Post by acoustibop on 2008-07-18
Exactly, Fran, I thought I needed a GUI 'till I tried Mednafen.

I also recall it was you who was kind enough to post a .deb for 0.8.8-1, the first version to work properly with SMS, for me. :)

---

### Post by minisori on 2008-07-18
> **tjwoosta said:**
> thanks for the repository, but i think im gonna try to stay away from mednafen 

(according to acoustibop it is "command line only")


**i need a GUI**

(not just for me but for all my cousins and nephews who love to play theese games)

A friend has almost finished a general purpose rom manager whit screenshots support, which can run the games with a simple click. You can setup there any emulator you want to use for a specific system.

He is working very hard in the GUI, to be very simple and try to share most of the options between emulators.

It uses clrmamepro romdats.


I still don't know when he will release it but what i have seen it's already working.

---

