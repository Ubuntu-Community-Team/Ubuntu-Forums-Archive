---
title: "TuxCube - GameCube emulator!"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2007-11-23
**[SIZE=5]PEOPLE TALKING ABOUT ROMS WILL GET REPORTED[/SIZE]**
Finally, a TuxCube source grab has been released! :KS
It's based on gcube, I've fixed some bugs. The project is intended to keep it alive so that we have a GameCube emulator on Linux in the future too!

Anyone wants to try it out? ;)

I've attached one screenshot (it's a bit old :P)

Libs required:
LibSDL dev
LibSDL_image dev

Latest version is pre1 (November 23rd)
Get it at [http://www.tuxemu.foo.se/](http://www.tuxemu.foo.se/) :guitar:

Video: [http://youtube.com/watch?v=vcqPkfgF6RU](http://youtube.com/watch?v=vcqPkfgF6RU)

---

### Post by go_beep_yourself on 2007-11-23
Yes, I would like to try that Zelda game out. However the website you provided will not load.

Firefox can't find the server at tuxemu.byethost31.com.

---

### Post by fearevilleet on 2007-11-23
I would like to try it out as well but your sites down.

---

### Post by Sockerdrickan on 2007-11-23
It works for me, this is weird

edit: [http://thepiratebay.org/tor/3904716](http://thepiratebay.org/tor/3904716)

---

### Post by hikaricore on 2007-11-23
Site loads for me as well.  Perhaps it's a pebkac issue?

*hides*

---

### Post by Sockerdrickan on 2007-11-23
Hahaha hikaricore, I love to learn new expressions like that. Keep em' coming.

---

### Post by go_beep_yourself on 2007-11-23
```
chris@ubuntu:~/Desktop/TuxEmu/tuxcube/source$ make    
Compiling: general.o
Compiling: config.o
video_sdl.c: In function 'video_init':
video_sdl.c:85: warning: pointer targets in passing argument 1 of 'strstr' differ in signedness
Compiling: audio_sdl.o
Compiling: cpu.o
Compiling: mem.o
Compiling: diskio.o
Compiling: hw.o
Compiling: hw_ai_dsp.o
Compiling: hw_cp.o
Compiling: hw_di.o
Compiling: hw_exi.o
Compiling: hw_gx.o
Compiling: hw_mi.o
Compiling: hw_pe.o
Compiling: hw_pi.o
Compiling: hw_si.o
Compiling: hw_vi.o
Compiling: hle.o
Compiling: hle_math.o
Compiling: hle_general.o
hle_general.c: In function 'HLE_OSReport_crippled':
hle_general.c:141: warning: cast from pointer to integer of different size
hle_general.c:147: warning: cast from pointer to integer of different size
hle_general.c:157: warning: cast to pointer from integer of different size
Compiling: gx.o
Compiling: gx_texture.o
Compiling: gx_transform.o
gcube.c: In function 'generate_map':
gcube.c:4692: warning: pointer targets in passing argument 1 of 'map_extract_db' differ in signedness
Linking... Done
chris@ubuntu:~/Desktop/TuxEmu/tuxcube/source$
```

Why does it compile with warnings?

---

### Post by go_beep_yourself on 2007-11-23
Why does the program come with an icon for the Applications menu if it must be used from the command line?

---

### Post by hikaricore on 2007-11-23
> **go_beep_yourself said:**
> ```
chris@ubuntu:~/Desktop/TuxEmu/tuxcube/source$ make    
Compiling: general.o
Compiling: config.o
video_sdl.c: In function 'video_init':
video_sdl.c:85: warning: pointer targets in passing argument 1 of 'strstr' differ in signedness
Compiling: audio_sdl.o
Compiling: cpu.o
Compiling: mem.o
Compiling: diskio.o
Compiling: hw.o
Compiling: hw_ai_dsp.o
Compiling: hw_cp.o
Compiling: hw_di.o
Compiling: hw_exi.o
Compiling: hw_gx.o
Compiling: hw_mi.o
Compiling: hw_pe.o
Compiling: hw_pi.o
Compiling: hw_si.o
Compiling: hw_vi.o
Compiling: hle.o
Compiling: hle_math.o
Compiling: hle_general.o
hle_general.c: In function 'HLE_OSReport_crippled':
hle_general.c:141: warning: cast from pointer to integer of different size
hle_general.c:147: warning: cast from pointer to integer of different size
hle_general.c:157: warning: cast to pointer from integer of different size
Compiling: gx.o
Compiling: gx_texture.o
Compiling: gx_transform.o
gcube.c: In function 'generate_map':
gcube.c:4692: warning: pointer targets in passing argument 1 of 'map_extract_db' differ in signedness
Linking... Done
chris@ubuntu:~/Desktop/TuxEmu/tuxcube/source$
```

Why does it compile with warnings?

Almost all software compiles with warnings of one kind or another.  These can usually be ignored.

---

### Post by Sockerdrickan on 2007-11-24
I have yet to eliminate the last few

---

### Post by Sockerdrickan on 2007-11-24
> **go_beep_yourself said:**
> Why does the program come with an icon for the Applications menu if it must be used from the command line?

It's not for the applications menu. It's for the actual app.

---

### Post by Extreme Coder on 2007-11-24
How's the compatibility though?

Can it run Zelda, or SSBM?

---

### Post by go_beep_yourself on 2007-11-24
> **Extreme Coder said:**
> How's the compatibility though?

Can it run Zelda, or SSBM?

What's SSBM? Super Smash Brothers Mario?

---

### Post by go_beep_yourself on 2007-11-24
It must be able to run Zelda because it is in the screenshot. It comes with a gameboy emulator also.

---

### Post by glosman15 on 2007-11-24
> **go_beep_yourself said:**
> What's SSBM? Super Smash Brothers Mario?

Super Smash Bros Melee.

---

### Post by Saint Nocturnal on 2007-12-06
Easy install. Stutters a bit with super smash bros on a AMD64 3700+, NV 7600GT. Might have to try it on the main machine. Is there a way to configure joystick button mapping? Only two buttons seem to work.

---

### Post by Sockerdrickan on 2007-12-06
I'll fix joypad stuff for the next source grab.

---

### Post by short3000y on 2007-12-06
how do you run it? instructions? sorry i still kinda new to linux...

---

### Post by Sockerdrickan on 2007-12-06
./TuxCube gamehere.gcm

---

### Post by short3000y on 2007-12-06
what do i do with that?

---

### Post by Sockerdrickan on 2007-12-07
Run it from a terminal in the TuxCube directory

---

### Post by svtfmook on 2007-12-07
does it run rom's, or can i use my gc discs?

---

### Post by Sockerdrickan on 2007-12-07
roms.

---

### Post by Extreme Coder on 2007-12-07
> **go_beep_yourself said:**
> It must be able to run Zelda because it is in the screenshot. It comes with a gameboy emulator also.
Well, how well it runs it is the real question.. I mean, it could just be able to reach the menu :P
It'd be nice if there was a compatibility list out there somewhere..

---

### Post by svtfmook on 2007-12-07
meh, i can't compile, get sdl/sdl_byteorder.h error

---

### Post by Danikar on 2007-12-08
Any word on this? If it is any good I'll play with it. heh.

---

### Post by Sockerdrickan on 2007-12-08
It should compile with no problems at all. This is pre-alpha though.

I wrote a new site [www.tuxemu.se.nu](www.tuxemu.se.nu) enjoy

---

### Post by Sarteck on 2007-12-08
Dude!  This is sweet!  :D  And here I thought I wouldn't be playing any Nintendo until I could afford a Wii.  ^_^  (And now I can use my BlackCats account for more than I previously was. XD)

When did you start this, anyway?  I wish I could help, but the only programming I know is for web **** anyway (though I'm teaching myself Python, and want to get into C++ next).  Still, if you need help with documentation, bandwidth, etc., I'd be more than willing to lend a hand.  :)

---

### Post by The Noble on 2007-12-08
Yeah, this looks pretty awsome. One question though: Tux0r, are you planning on becoming the main developer or is this a port? Should we expect further improvements with compatibility? (I know that was two questions, but whatever) Either way, thanks for porting this over to linux. One day we'll have the gamecube fully emulated, and I'm looking forward to that.

---

### Post by gcrussell1 on 2007-12-08
> **The Noble said:**
> Yeah, this looks pretty awsome. One question though: Tux0r, are you planning on becoming the main developer or is this a port? Should we expect further improvements with compatibility? (I know that was two questions, but whatever) Either way, thanks for porting this over to linux. One day we'll have the gamecube fully emulated, and I'm looking forward to that.

Fully emulated? :neutral: The NES still isn't fully emulated... the best that might be hoped for is that an emulator will eventually be created (with necessary plugins if it uses them) that runs all existing games with no problems. Even then, someone could develop a GC game (not that they would develop for a dead system by the time this dream is realized) that would not run on the emulator, but would run perfectly on the system. That's why, for example, almost everything but Star Ocean ran perfectly on ZSNES a couple years ago, but Star Ocean didn't run at all.

Sorry if I'm just splitting hairs, but that's my two cents.

---

### Post by The Noble on 2007-12-09
Heh, no problem. I was guessing someone would point that out. What I meant was just "reasonably compatible", like the playstation emulators currently are.

---

### Post by Bionic Apple on 2007-12-09
I get this after trying to compile it (nothing is produced from it):


```
name@computer:~$ cd ~/Desktop/tuxcube/source/
name@computer:~/Desktop/tuxcube/source$ make
In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:5:20: error: stdlib.h: No such file or directory
general.h:6:20: error: string.h: No such file or directory
general.h:7:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from general.h:8,
                 from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:9:22: error: sys/stat.h: No such file or directory
general.h:21:31: error: SDL/SDL_byteorder.h: No such file or directory
ppc_disasm.c:122: error: ‘NULL’ undeclared here (not in a function)
ppc_disasm.c: In function ‘spr_name’:
ppc_disasm.c:250: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ill’:
ppc_disasm.c:275: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c:276: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘imm’:
ppc_disasm.c:301: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ra_rb’:
ppc_disasm.c:323: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘rd_ra_rb’:
ppc_disasm.c:332: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘fd_ra_rb’:
ppc_disasm.c:352: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘trapi’:
ppc_disasm.c:371: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘cmpi’:
ppc_disasm.c:386: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘addi’:
ppc_disasm.c:401: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:408: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘branch’:
ppc_disasm.c:433: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:436: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:442: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:451: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘bc’:
ppc_disasm.c:473: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘bli’:
ppc_disasm.c:486: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘mcrf’:
ppc_disasm.c:499: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘crop’:
ppc_disasm.c:514: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘nooper’:
ppc_disasm.c:532: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c: In function ‘rlw’:
ppc_disasm.c:545: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ori’:
ppc_disasm.c:552: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c: In function ‘rld’:
ppc_disasm.c:565: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘cmp’:
ppc_disasm.c:578: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c:580: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘trap’:
ppc_disasm.c:595: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:602: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c:606: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c: In function ‘dab’:
ppc_disasm.c:625: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘rrn’:
ppc_disasm.c:645: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘mtcr’:
ppc_disasm.c:663: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘msr’:
ppc_disasm.c:681: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘mspr’:
ppc_disasm.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘mtb’:
ppc_disasm.c:745: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘sradi’:
ppc_disasm.c:771: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ldst_offs’:
ppc_disasm.c:787: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:793: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:797: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ldst’:
ppc_disasm.c:814: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c:817: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:821: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘fdabc’:
ppc_disasm.c:833: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘fdab’:
ppc_disasm.c:855: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c: In function ‘fcmp’:
ppc_disasm.c:865: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘mtfsb’:
ppc_disasm.c:878: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_cmpx’:
ppc_disasm.c:891: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_ldst_offs’:
ppc_disasm.c:907: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:913: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:917: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_ldst’:
ppc_disasm.c:929: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_ldstx’:
ppc_disasm.c:936: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_dacb’:
ppc_disasm.c:944: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_dac’:
ppc_disasm.c:954: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_dab’:
ppc_disasm.c:964: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘ps_db’:
ppc_disasm.c:974: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c: In function ‘PPC_Disassemble’:
ppc_disasm.c:1131: warning: incompatible implicit declaration of built-in function ‘strcpy’
ppc_disasm.c:1717: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:2103: warning: incompatible implicit declaration of built-in function ‘sprintf’
ppc_disasm.c:2128: warning: incompatible implicit declaration of built-in function ‘sprintf’
make: *** [ppc_disasm.o] Error 1

```

---

### Post by Sockerdrickan on 2007-12-09
Bionic Apple if you don't have stdlib.h you probably need to get g++ and other stuff like binutils

---

### Post by Bionic Apple on 2007-12-09
Now I am getting this error:

```
name@computer:~$ cd ~/Desktop/tuxcube/source/
name@computer:~/Desktop/tuxcube/source$ make
In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:21:31: error: SDL/SDL_byteorder.h: No such file or directory
make: *** [ppc_disasm.o] Error 1
```

---

### Post by Sockerdrickan on 2007-12-09
Do you have libsdl dev

---

### Post by go_beep_yourself on 2007-12-09
What format should the games be in? I tried ripping my zelda wind walker game to iso. That iso wouldn't run with the emulator.

---

### Post by k0rfain on 2007-12-09
```
Compiling: config.o
video_sdl.c:3:27: error: SDL/SDL_image.h: No such file or directory
video_sdl.c: In function ‘video_set_icon’:
video_sdl.c:27: warning: assignment makes pointer from integer without a cast
video_sdl.c:28: warning: assignment makes pointer from integer without a cast
video_sdl.c: In function ‘video_init’:
video_sdl.c:85: warning: pointer targets in passing argument 1 of ‘strstr’ differ in signedness
make: *** [video_sdl.o] Error 1

```

waaaaaaaaaaaaa

---

### Post by Sockerdrickan on 2007-12-09
Install libsdl_image dev

---

### Post by k0rfain on 2007-12-09
thanks, do you know any websites i where i can get roms for this

---

### Post by UK-Wobbie on 2007-12-09
> **Tux0r said:**
> Finally, a TuxCube source grab has been released! :KS
It's based on gcube, I've fixed some bugs. The project is intended to keep it alive so that we have a GameCube emulator on Linux in the future too!

Anyone wants to try it out? ;)

I've attached one screenshot (it's a bit old :P)

Libs required:
LibSDL dev
LibSDL_image dev

Latest version is pre1 (November 23rd)
Get it at [http://www.tuxemu.se.nu/](http://www.tuxemu.se.nu/) :guitar:

Video: [http://youtube.com/watch?v=vcqPkfgF6RU](http://youtube.com/watch?v=vcqPkfgF6RU)

Thats cool :mrgreen:
How do i make my own ISO of GameCube games? 
Any one know? :lolflag:

---

### Post by Sockerdrickan on 2007-12-09
This forum is not intended for these type of questions. [www.google.com](www.google.com)

---

### Post by Bionic Apple on 2007-12-09
> **Tux0r said:**
> Do you have libsdl dev

Thanks, that worked.

---

### Post by Sarteck on 2007-12-10
Hey, Tux0r, what's the news?  What are you going to be working on for this?  Anything in the way of a GUI configuration?  (I finally figured out where to configure what, but I hate having to look up what keys are what keycodes, and ditto for the USB controller I'm now trying to configure).  Heck, I guess even a command-line config utility would be nice, heh.

---

### Post by Sarteck on 2007-12-10
> **UK-Wobbie said:**
> Thats cool :mrgreen:
How do i make my own ISO of GameCube games? 
Any one know? :lolflag:
Actually, Wobbie, I'm not sure that it plays ISOs.  I think it's just GCM files.  (I might be wrong.)

I think, also, that afterdawn has a few GCM howtos.

---

### Post by short3000y on 2007-12-11
i get an error when i try to do the make command, HELP!!!!!! <<<total nuub

---

### Post by short3000y on 2007-12-11
how do i get>>>

Libs required:
LibSDL dev
LibSDL_image dev

---

### Post by hikaricore on 2007-12-11
This has already been covered atleast once in this very thread.

---

### Post by short3000y on 2007-12-11
ok after googling awhile, i got those 2, now when i try to launch the game i get this error>

bash: ./TuxCube: No such file or directory

---

### Post by short3000y on 2007-12-11
i also get the error 
takkune@Canti-laptop:~/Desktop/tuxcube$ ./TuxCube awesome_game.gcm
can't open file awesome_game.gcm
takkune@Canti-laptop:~/Desktop/tuxcube$

---

### Post by Sockerdrickan on 2007-12-11
> **Sarteck said:**
> Hey, Tux0r, what's the news?  What are you going to be working on for this?  Anything in the way of a GUI configuration?  (I finally figured out where to configure what, but I hate having to look up what keys are what keycodes, and ditto for the USB controller I'm now trying to configure).  Heck, I guess even a command-line config utility would be nice, heh.
I'm a bit busy with school right now, but soon it'll cool down. :)

> **short3000y said:**
> i also get the error 
takkune@Canti-laptop:~/Desktop/tuxcube$ ./TuxCube awesome_game.gcm
can't open file awesome_game.gcm
takkune@Canti-laptop:~/Desktop/tuxcube$

Are you saying you have a game called awesome_game.gcm? Because I doubt that.

---

### Post by treeko11 on 2007-12-11
tux0r, i was wondering if you could post a compatability list for all of us?

Thanks, treeko11

---

### Post by Shinbu-Otaku on 2007-12-11
oh wow a GC emulator, i didnt even know these were possible (i've never heard of 1 before lol)

good work :D

---

### Post by lespaul_rentals on 2007-12-11
Nice job!  Thanks for your contribution.  :KS

I haven't been able to download it yet.  Is it written in C++, Python, what?

---

### Post by snickers295 on 2007-12-11
when i download it it takes me to a page with a bunch of binary (#$#141 for those of you who don't know what it looks like)
i save the thing to my computer and it still is the same.

---

### Post by Sockerdrickan on 2007-12-11
You need 7zip

---

### Post by Sarteck on 2007-12-11
Nah, Tux0r, it did the same for me, and I have 7zip.  :)

snickers295, you just need to right-click on the link in FireFox and choose to "Save Link As..."  Then you can download it.  :)

---

### Post by Vadi on 2007-12-11
This looks really great, but I don't have any rom images. Tux0r, I hope you make more games though, the quality is looking awesome :)

---

### Post by PriceChild on 2007-12-11
No rom requests, lets keep this legal please

---

### Post by Sockerdrickan on 2007-12-11
> **Sarteck said:**
> Nah, Tux0r, it did the same for me, and I have 7zip.  :)

snickers295, you just need to right-click on the link in FireFox and choose to "Save Link As..."  Then you can download it.  :)

I meant as in opening the actual file. I don't know why Firefox behaves this way.

> **Vadi said:**
> This looks really great, but I don't have any rom images. Tux0r, I hope you make more games though, the quality is looking awesome :)

I don't make the games :P It's an emulator, remember? :)

---

### Post by Vadi on 2007-12-11
Well, yeah. You should make games then!

---

### Post by Sockerdrickan on 2007-12-11
I am, not for GameCube, though. :)

---

### Post by vparask on 2007-12-25
i write "exec ./TuxCube awesome_game.gcm" but the terminal windows closed. what can i do;

---

### Post by go_beep_yourself on 2007-12-25
> **vparask said:**
> i write "exec ./TuxCube awesome_game.gcm" but the terminal windows closed. what can i do;

Run it with strace.

strace ./TuxCube awesome_game.gcm

---

### Post by lagooned on 2007-12-25
use this to install the dependencies:
sudo apt-get install libsdl-image1.2-dev libsdl1.2-dev
that'll work for ubuntu, anyway 
really good emulator, i was kinda disapointed that he dropped the project
but it was searchin and i found this, i praised god.
thank you for continuing the project!

:D

---

### Post by anonymous131 on 2007-12-27
How am I supposed to compile this code?
With what program and how?

---

### Post by anonymous131 on 2007-12-27
Okay, it closed on me, so I ran it w/ strace:
(Ignore the picture underneath)

I get the same thing when I strace ./TuxCube


```
paul@paul-desktop:~/Desktop/tuxcube$ strace ./TuxCube awesome_game.gcm
execve("./TuxCube", ["./TuxCube", "awesome_game.gcm"], [/* 35 vars */]) = 0
brk(0)                                  = 0x17030000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fae000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=62891, ...}) = 0
mmap2(NULL, 62891, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f9e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libSDL-1.2.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0pd\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=420760, ...}) = 0
mmap2(NULL, 584624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f0f000
mmap2(0xb7f74000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x65) = 0xb7f74000
mmap2(0xb7f76000, 162736, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f76000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=80504, ...}) = 0
mmap2(NULL, 83232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7efa000
mmap2(0xb7f0e000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7f0e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\275"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=386556, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef9000
mmap2(NULL, 394792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e98000
mmap2(0xb7ef6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5d) = 0xb7ef6000
mmap2(0xb7ef8000, 1576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ef8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libSDL_image-1.2.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\30"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=43000, ...}) = 0
mmap2(NULL, 109008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e7d000
mmap2(0xb7e87000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb7e87000
mmap2(0xb7e88000, 63952, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e88000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d33000
mmap2(0xb7e77000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7e77000
mmap2(0xb7e7a000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e7a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149332, ...}) = 0
mmap2(NULL, 147584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d0e000
mmap2(0xb7d31000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb7d31000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240,\2"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=806112, ...}) = 0
mmap2(NULL, 809016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c48000
mmap2(0xb7d09000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc0) = 0xb7d09000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c44000
mmap2(0xb7c46000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7c46000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdirectfb-0.9.so.25", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\261"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=354504, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c43000
mmap2(NULL, 354564, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bec000
mmap2(0xb7c41000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x55) = 0xb7c41000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libfusion-0.9.so.25", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\35\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=20388, ...}) = 0
mmap2(NULL, 23276, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7be6000
mmap2(0xb7beb000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4) = 0xb7beb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdirect-0.9.so.25", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P/\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=59832, ...}) = 0
mmap2(NULL, 60716, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bd7000
mmap2(0xb7be5000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe) = 0xb7be5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112423, ...}) = 0
mmap2(NULL, 94688, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bbf000
mmap2(0xb7bd3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7bd3000
mmap2(0xb7bd5000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7bd5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240s\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=986540, ...}) = 0
mmap2(NULL, 986876, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ace000
mmap2(0xb7bbb000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xed) = 0xb7bbb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220*\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=56156, ...}) = 0
mmap2(NULL, 55228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ac0000
mmap2(0xb7acd000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xb7acd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXxf86vm.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=16220, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7abf000
mmap2(NULL, 19068, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7aba000
mmap2(0xb7abe000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7abe000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXdamage.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\7\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=5992, ...}) = 0
mmap2(NULL, 8932, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ab7000
mmap2(0xb7ab9000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7ab9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXfixes.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\16\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=14128, ...}) = 0
mmap2(NULL, 17116, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ab2000
mmap2(0xb7ab6000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7ab6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdrm.so.2", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \'\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34556, ...}) = 0
mmap2(NULL, 38760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7aa8000
mmap2(0xb7ab1000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7ab1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpng12.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240=\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=139768, ...}) = 0
mmap2(NULL, 142680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7a85000
mmap2(0xb7aa7000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x21) = 0xb7aa7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\10"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=6988, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7a84000
mmap2(NULL, 9928, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7a81000
mmap2(0xb7a83000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7a83000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \16\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=16616, ...}) = 0
mmap2(NULL, 19544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7a7c000
mmap2(0xb7a80000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7a80000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7a7b000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7a7a000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7a7a6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7e77000, 4096, PROT_READ)   = 0
mprotect(0xb7e98000, 385024, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7e98000, 385024, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7f0f000, 413696, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7f0f000, 413696, PROT_READ|PROT_EXEC) = 0
munmap(0xb7f9e000, 62891)               = 0
set_tid_address(0xb7a7a6f8)             = 11500
set_robust_list(0xb7a7a700, 0xc)        = 0
rt_sigaction(SIGRTMIN, {0xb7bc3300, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7bc3380, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="paul-desktop", ...}) = 0
mkdir("/home/paul/.tuxcube-", 0755)     = -1 EEXIST (File exists)
mkdir("/home/paul/.tuxcube-/maps", 0755) = -1 EEXIST (File exists)
mkdir("/home/paul/.tuxcube-/screenshots", 0755) = -1 EEXIST (File exists)
brk(0)                                  = 0x17030000
brk(0x17051000)                         = 0x17051000
open("awesome_game.gcm", O_RDONLY)      = -1 ENOENT (No such file or directory)
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fad000
write(1, "can\'t open file awesome_game.gcm"..., 33can't open file awesome_game.gcm
) = 33
exit_group(0)                           = ?
Process 11500 detached
paul@paul-desktop:~/Desktop/tuxcube$ 
paul@paul-desktop:~/Desktop/tuxcube$
```

---

### Post by Sockerdrickan on 2007-12-27
I have no idea what you guys are doing.

Why run it with strace?

./TuxCube awesome_game.gcm

awesome_game.gcm is where you put your game. it's not some kind of options startup flag (why would you think that?!)

---

### Post by anonymous131 on 2007-12-28
What? Instructions please...

I put my game there and it won't work.

I tried it w/ strace because of post #61 told me to.

---

### Post by Sockerdrickan on 2007-12-28
./TuxCube game.gcm
that works trust me, replace game with the file

---

### Post by anonymous131 on 2007-12-28
It doesn't work for me...
GAAAAAAAAh

---

### Post by KCPokes on 2007-12-28
What is the filename you are copying your game over as?  It tells you in the strace, and should in the terminal as well, that it cannot find the file, whether it be awesome_game.gcm or game.gcm.  

```

./TuxCube <gcm game here>

```

Do not take the awesome_game.gcm or game.gcm as literals; they are examples.

---

### Post by Sockerdrickan on 2007-12-28
This will be more usable when the GUI is done.

---

### Post by anonymous131 on 2007-12-28
Aughhh... I don't get any of this...
Am I supposed to run strace or what?
I put in your given code and it still doesn't open. =(

---

### Post by Sockerdrickan on 2007-12-30
1. Don't run it with strace
2. ```
./TuxCube <gcm game here>
```

---

### Post by Twintop on 2007-12-30
Thanks Tux0r! Now all I need is a GC -> USB adapter...

---

### Post by Sockerdrickan on 2007-12-30
PM me if you find one! ;)

---

### Post by Dark Aspect on 2008-01-05
I get this in the terminal when I try to compile tuxcube:

> In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:21:31: error: SDL/SDL_byteorder.h: No such file or directory
make: *** [ppc_disasm.o] Error 1

What am I doing wrong?I am running Ubuntu 7.10 64-bit.

EDIT:Nevermind......I fixed it

---

### Post by RevolutionMaster on 2008-01-06
is there a way to "rip" a gamecube disc into this.

---

### Post by RevolutionMaster on 2008-01-06
gcube emulation flat out sucks on a keyboard. Is there a way to create a gamecube to USB adapter?

---

### Post by Dark Aspect on 2008-01-08
Resident Evil Zero does not load.......It stalls at a black screen saying 16-18 frame per seconds.

---

### Post by sup_dawg444 on 2008-03-30
> **Dark Aspect said:**
> I get this in the terminal when I try to compile tuxcube:


What am I doing wrong?I am running Ubuntu 7.10 64-bit.

EDIT:Nevermind......I fixed it

What exactly did you do? I'm getting the same error.

I'm kind of new at Linux so... go easy on me.

---

### Post by grossaffe on 2008-03-30
> **RevolutionMaster said:**
> gcube emulation flat out sucks on a keyboard. Is there a way to create a gamecube to USB adapter?

i've seen GC/PS2/XBOX to USB adaptors for like $5 at walmart (or maybe $10, not sure).

if you were to build one by hand, i think you'd need a specialized device that can program USB thingies which would cost your somewhere around $80 or so.  unless you plan on building a lot of different USB thingies, i'd go with the $10 walmart adapter.

---

### Post by grossaffe on 2008-04-26
> **RevolutionMaster said:**
> is there a way to "rip" a gamecube disc into this.

i read that there's a way to do it through Phantasy Star Online.  it involves a network adaptor and some other stuff.  basically you trick the system into thinking its transferring information to a game server or something, but its really transferring the contents of whatever disk you have in there.

---

### Post by grossaffe on 2008-04-29
I finally got a .gcm file to test tuxcube with, but i'm not entirely sure of the controls.  how do you do stuff?  i think i figured up some of the buttons, but i really need the joystick controls.  i have SSBM, but you can't really do anything without choosing a character, which you can't do without the joystick.

---

### Post by wolffangalchemist on 2008-05-14
can someone supply me with a already compied one? 
it refuses to compile in my computer for some reson.
i get this .
```
wolffangalchemist@wolffangalchemist-desktop:~$ cd Desktop/tuxcube/source
wolffangalchemist@wolffangalchemist-desktop:~/Desktop/tuxcube/source$ make
In file included from ppc_disasm.h:5,
                 from ppc_disasm.c:48:
general.h:21:31: error: SDL/SDL_byteorder.h: No such file or directory
make: *** [ppc_disasm.o] Error 1
wolffangalchemist@wolffangalchemist-desktop:~/Desktop/tuxcube/source$ 

```

---

### Post by Sockerdrickan on 2008-05-15
Get libsdl1.2-dev

---

### Post by Vadi on 2008-05-15
You can ask getdeb.net to make a .deb (use their contacts link on [www.getdeb.net](www.getdeb.net))

---

### Post by grossaffe on 2008-05-15
so, um... how do you set up a joystick to work with this?

---

### Post by wolffangalchemist on 2008-05-16
> **grossaffe said:**
> so, um... how do you set up a joystick to work with this?

i was just about to ask the same thing.

---

### Post by cor2y on 2008-06-19
Its still alpha guys and thus not completely ready for general usage.
So far i have determined that the "s" key is for start.
It does work but my system doesn't seem to be up to running a gc rom at full speed, i made it through the wind waker intro and start screen but it was running to slow and the colors and sprites looked odd to be of any use to say playing a game.
So just wait for the update.

---

### Post by Zeotronic on 2008-06-19
Holy crap, somebody actually salvaged GCube!? This is a happy day... my computer will probably never be able to run it, but this is still a happy day.

---

### Post by atdesantis11 on 2008-07-20
andrewdesantis@andrewdesantis-laptop:~$ cd Desktop/tuxcube/source
andrewdesantis@andrewdesantis-laptop:~/Desktop/tuxcube/source$ make
Compiling: config.o
In file included from hw_di.h:5,
                 from mem.h:12,
                 from video.h:7,
                 from config.h:9,
                 from config.c:1:
diskio.h:6:18: error: zlib.h: No such file or directory
make: *** [config.o] Error 1
andrewdesantis@andrewdesantis-laptop:~/Desktop/tuxcube/source$ 

whats wrong?

---

### Post by Sockerdrickan on 2008-07-21
```
sudo apt-get install zlib1g-dev
```

---

### Post by atdesantis11 on 2008-07-21
andrewdesantis@andrewdesantis-laptop:~$ sudo apt-get install zliblg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zliblg-dev

---

### Post by Sockerdrickan on 2008-07-21
That's not an L it's a ONE

---

### Post by GepettoBR on 2008-09-14
Bumping to keep thread alive. What's the current status of the project, or where can I find out myself? Google has only pointed me to this thread and a bunch of old stuff.

---

### Post by Sockerdrickan on 2008-09-14
Watch for news at [www.tuxemu.se.nu]("http://www.tuxemu.se.nu") is all I can say, right now I'm a bit tied up with another project I'm writing from scratch. :popcorn:

[IMG]http://img26.picoodle.com/data/img26/3/9/14/f_SkrmbildPokm_e5ca892.png[/IMG]    [IMG]http://img37.picoodle.com/data/img37/3/9/14/f_SkrmbildPokm_b66555d.png[/IMG]

---

### Post by grossaffe on 2008-09-16
> **Tux0r said:**
> Watch for news at [www.tuxemu.se.nu]("http://www.tuxemu.se.nu") is all I can say, right now I'm a bit tied up with another project I'm writing from scratch. :popcorn:

[IMG]http://img26.picoodle.com/data/img26/3/9/14/f_SkrmbildPokm_e5ca892.png[/IMG]    [IMG]http://img37.picoodle.com/data/img37/3/9/14/f_SkrmbildPokm_b66555d.png[/IMG]

That's quite the interesting project.  I just assumed that was one of the newer pokemon games I'd never played from looking at the screen shots you have.

---

### Post by GepettoBR on 2008-09-16
Thanks for the link, and good luck in all your projects!

---

### Post by flanker711 on 2008-11-23
Does tuxcube support Mario Cart double dash for gamecube?

> **Tux0r said:**
> Watch for news at [www.tuxemu.se.nu]("http://www.tuxemu.se.nu") is all I can say, right now I'm a bit tied up with another project I'm writing from scratch. :popcorn:

[IMG]http://img26.picoodle.com/data/img26/3/9/14/f_SkrmbildPokm_e5ca892.png[/IMG]    [IMG]http://img37.picoodle.com/data/img37/3/9/14/f_SkrmbildPokm_b66555d.png[/IMG]

---

### Post by Hemen on 2008-12-27
I have installed in on ubuntu.

But how do i play games on Tuxcube? I did find a file named Tuxcube but it won't start.

So how do i play games on Tuxcube? 
And yes i have the iso file on my Computer, i just need to know how to play it on Tuxcube.

---

### Post by gtfunding on 2009-01-15
Any one tried Dolphin?

---

### Post by dragos240 on 2009-03-29
> **Hemen said:**
> I have installed in on ubuntu.

But how do i play games on Tuxcube? I did find a file named Tuxcube but it won't start.

So how do i play games on Tuxcube? 
And yes i have the iso file on my Computer, i just need to know how to play it on Tuxcube.

Usage:
./TuxCube zeldawindwaker.gcm

it looks in the tuxcube directory for the game, although i recommend putting it in the roms directory and running it like this:

./TuxCube roms/zeldawindwaker.gcm

also it may be nessisary to replace "zeldawindwaker.gcm" (without quotes) with your rom file, if it ends in iso you will need to rename it to gcm.
WARNING! SLOOOOOOOW!

---

### Post by Utsukushii Tsubasa on 2009-06-19
soo yea, can someone give me step by step instructions?
im so confused on what to do right now. lol
also a question mixed in, does it come with games, or where can i find them? 
all help is appreciated.

---

### Post by GepettoBR on 2009-06-19
> **Utsukushii Tsubasa said:**
> soo yea, can someone give me step by step instructions?
im so confused on what to do right now. lol
also a question mixed in, does it come with games, or where can i find them? 
all help is appreciated.

It doesn't come with games. You need a way to mount an actual Gamecube disc or to rip it into an image and mount that.

---

### Post by Utsukushii Tsubasa on 2009-06-19
k. still need help installing ^^

---

### Post by tommah04 on 2009-07-05
change to directory where tuxcube's source folder is

then type "make"

---

### Post by beliyyal on 2009-09-18
```
dalton@Astaroth:~/tuxcube/source$ make
Compiling: video_sdl.o
video_sdl.c:3:27: error: SDL/SDL_image.h: No such file or directory
video_sdl.c: In function ‘video_set_icon’:
video_sdl.c:27: warning: assignment makes pointer from integer without a cast
make: *** [video_sdl.o] Error 1
dalton@Astaroth:~/tuxcube/source$
```

can someone help me out here?

---

### Post by Perfect Storm on 2009-09-18
> **beliyyal said:**
> ```
dalton@Astaroth:~/tuxcube/source$ make
Compiling: video_sdl.o
video_sdl.c:3:27: error: SDL/SDL_image.h: No such file or directory
video_sdl.c: In function &#8216;video_set_icon&#8217;:
video_sdl.c:27: warning: assignment makes pointer from integer without a cast
make: *** [video_sdl.o] Error 1
dalton@Astaroth:~/tuxcube/source$
```

can someone help me out here?

As OP said it requires that you install

LibSDL dev
LibSDL_image dev

---

### Post by kforum on 2009-09-20
isnt dolphin a better emulator to base on?

---

### Post by CharmyBee on 2009-09-20
> **kforum said:**
> isnt dolphin a better emulator to base on?

Yes, though even Dolphin isn't playable with everything, but it's a universally better choice than old TuxCube.

---

### Post by SAFAD on 2009-09-29
Cool Man
Can It Run Resident Evil 0 And Remake ?
I Tried Dolphin In WinSux But It Runs In Low FPS
30-25

---

### Post by gcbzzzz on 2009-11-20
No. Use dolphin. kthxby


[http://code.google.com/p/dolphin-emu/](http://code.google.com/p/dolphin-emu/)

---

### Post by johnboy1313 on 2009-11-20
> **Tux0r said:**
> **[SIZE=5]PEOPLE TALKING ABOUT ROMS WILL GET REPORTED[/SIZE]**
Finally, a TuxCube source grab has been released! :KS
It's based on gcube, I've fixed some bugs. The project is intended to keep it alive so that we have a GameCube emulator on Linux in the future too!

Anyone wants to try it out? ;)

I've attached one screenshot (it's a bit old :P)

Libs required:
LibSDL dev
LibSDL_image dev

Latest version is pre1 (November 23rd)
Get it at [http://www.tuxemu.foo.se/](http://www.tuxemu.foo.se/) :guitar:

Video: [http://youtube.com/watch?v=vcqPkfgF6RU](http://youtube.com/watch?v=vcqPkfgF6RU)

this makes me happy! i will be downloading

---

### Post by Akira Takano on 2009-11-24
> **Tux0r said:**
> **[SIZE=5]PEOPLE TALKING ABOUT ROMS WILL GET REPORTED[/SIZE]**
Finally, a TuxCube source grab has been released! :KS
It's based on gcube, I've fixed some bugs. The project is intended to keep it alive so that we have a GameCube emulator on Linux in the future too!

Anyone wants to try it out? ;)

I've attached one screenshot (it's a bit old :P)

Libs required:
LibSDL dev
LibSDL_image dev

Latest version is pre1 (November 23rd)
Get it at [http://www.tuxemu.foo.se/](http://www.tuxemu.foo.se/) :guitar:

Video: [http://youtube.com/watch?v=vcqPkfgF6RU](http://youtube.com/watch?v=vcqPkfgF6RU)

i can't find the download on this site.

---

### Post by emeraldgirl08 on 2009-11-25
:popcorn:

Real nice! Thankfully I still have an authentic Gamecube and a copy of Windwaker on standby if the urge hits :)

---

