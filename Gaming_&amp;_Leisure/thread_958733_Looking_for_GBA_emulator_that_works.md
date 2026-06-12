---
title: "Looking for GBA emulator that works"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by grossaffe on 2008-10-25
I've been trying to get a GBA emulator, but I none of them seem to work for me.  the only ones that I can get trying to run are derived from VBA, but all it does is open up a blank window that won't close.  I know the ROMS aren't the problem since I was able to get them to run on a GBA emulator through WINE, but I would prefer a linux-native program.

so... what are my options for GBA emulator in Linux that will actually work?  don't know if it matters, but I am running 64-bit.

---

### Post by Sockerdrickan on 2008-10-25
VBA-M hands down

---

### Post by grossaffe on 2008-10-25
> **Tux0r said:**
> VBA-M hands down

I looked into that but only saw windows binaries.  Think you could direct me to a place to find what I need to get it on Linux?

---

### Post by FranMichaels on 2008-10-25
[mednafen]("http://mednafen.sourceforge.net/"). It's in the repos.

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> [mednafen]("http://mednafen.sourceforge.net/"). It's in the repos.

does it have any kind of front-end or is it all command-line?

---

### Post by Hyper Tails on 2008-10-25
Go to add/remove programs and type in Visual, and then go to games, then check VBA Express

that my friend is an gba emulator

no wine needed

enjoy ;)

---

### Post by grossaffe on 2008-10-25
Okay, I'm having serious problems.  Every single linux-native GBA emulator that I've install is just giving me a blank screen.  Already tried VBA, VBA-express, gnomeboy, VGBA, boycott advance, and now even mednafen.  I swear I've gotten these roms to work in an emulator through WINE, so I must have a problem somewhere.

---

### Post by FranMichaels on 2008-10-25
> **grossaffe said:**
> Okay, I'm having serious problems.  Every single linux-native GBA emulator that I've install is just giving me a blank screen.  Already tried VBA, VBA-express, gnomeboy, boycott advance, and now even mednafen.  I swear I've gotten these roms to work in an emulator through WINE, so I must have a problem somewhere.

There is a front-end on the forums here somewhere, just press f1 to view the hotkeys after you load your game. 

Are your roms compressed in some odd format? I think most emulators handle things in .zip and .gz. What does the emulator show if you run it from terminal. Maybe there is a video driver problem? Since so many programs are effected...

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> There is a front-end on the forums here somewhere, just press f1 to view the hotkeys after you load your game. 

Are your roms compressed in some odd format? I think most emulators handle things in .zip and .gz. What does the emulator show if you run it from terminal. Maybe there is a video driver problem? Since so many programs are effected...

running mednafen in command:
```
Starting Mednafen 0.8.7
 Loading settings from "/home/christian/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.12, running with SDL 1.2.12

 Initializing joysticks...
  Joystick 0 - Logitech Logitech RumblePad 2 USB - Unique ID: ce96ea6b9d7ca56a
 Loading ./Desktop/games/gameboy/ROMS/PokemonEmerald.gba...

  ROM:       16384KiB
  ROM CRC32: 0x1f1c08fb
  ROM MD5:   0x605b89b67018abcea91e693a4dd25be3

  Loading cheats from /home/christian/.mednafen/cheats/gba.cht...
   Error opening file: No such file or directory

 Initializing sound...
  Using "ALSA" audio driver with device "default":
   Bits: 16
   Rate: 48000
   Channels: 2
   Byte order: CPU Native
   Buffer size: 1536 sample frames(32.000000 ms)
 Initializing video...
  Video Mode: 720 x 480 x 32 bpp
  OpenGL: Yes
   Pixel shader: none
  Fullscreen: No
  Special Scaler: None
  Scanlines: Off
  Destination Rectangle: X=0, Y=0, W=720, H=480
  OpenGL Implementation: NVIDIA Corporation GeForce 8400M GS/PCI/SSE2 2.1.2 NVIDIA 169.12
  Checking extensions:
   GL_ARB_texture_non_power_of_two found.
  Using non-power-of-2 sized textures.
  Checking maximum texture size...
   Apparently it is at least: 8192 x 8192
SRAM emulation disabled by write to:  0e005555 000000aa

```

only error I see is from not having a cheat folder

---

### Post by FranMichaels on 2008-10-25
Alright, well it shows you have a proprietary video driver, so I'm going to assume that's the issue. ;)

Try
```
gedit ~/.mednafen/mednafen.cfg
```

Find
> ;Select video driver, "opengl" or "sdl".
vdriver 0


Change 0 to 1.

Try and see. If that fixes it, then for sure it's related to the video driver...

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> Alright, well it shows you have a proprietary video driver, so I'm going to assume that's the issue. ;)

Try
```
gedit ~/.mednafen/mednafen.cfg
```

Find


Change 0 to 1.

Try and see. If that fixes it, then for sure it's related to the video driver...

that part of the file actually says this:
```
;Select video driver, "opengl" or "sdl".
vdriver opengl
```
so should I change it to sdl?

just curious, would compiz possibly cause this problem?

---

### Post by FranMichaels on 2008-10-25
> **grossaffe said:**
> that part of the file actually says this:
```
;Select video driver, "opengl" or "sdl".
vdriver opengl
```
so should I change it to sdl?

just curious, would compiz possibly cause this problem?

Ah, you have 0.8.7, I have mednafen 0.8.9, probably just a config file change... Go for it and see if changing the value helps.

I can run mednafen with or without compiz (have mobile intel 945gm on board... not fantastic, but has free drivers so...) You can try turning off compiz and launching as is... 

Troubleshooting is fun... ;)

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> Ah, you have 0.8.7, I have mednafen 0.8.9, probably just a config file change... Go for it and see if changing the value helps.

I can run mednafen with or without compiz (have mobile intel 945gm on board... not fantastic, but has free drivers so...) You can try turning off compiz and launching as is... 

Troubleshooting is fun... ;)
I installed from synaptec, so whatever version was in there...

anyways, I just tried sdl and that didn't work either.

---

### Post by FranMichaels on 2008-10-25
> **grossaffe said:**
> I installed from synaptec, so whatever version was in there...

anyways, I just tried sdl and that didn't work either.

And you tried with compiz off too?

Okay, go ahead and set it back to opengl.

Try another rom if possible, perhaps your pokemon one requires a gba.bios. Yes, yes forum rules, don't ask about it here, just use google etc...

If it is still messed up... I don't know, how can it effect so many native emulators, yet work in wine... I'm at a loss honestly...

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> And you tried with compiz off too?

Okay, go ahead and set it back to opengl.

Try another rom if possible, perhaps your pokemon one requires a gba.bios. Yes, yes forum rules, don't ask about it here, just use google etc...

If it is still messed up... I don't know, how can it effect so many native emulators, yet work in wine... I'm at a loss honestly...

before I turn off compiz, how do I do it so that I don't have to redo all my settings in it when I turn it back on?

---

### Post by FranMichaels on 2008-10-25
It shouldn't remove any settings if you do it manually. If you are really worried, you can make a quick tarball of your .compiz folder.

What I use at before I run the emulator
```
metacity --replace &
```
then after
```
compiz --replace &
```

(Well I have it automated with a small zenity script, so I can just type a few letters of the game name, then double click the result, and the right emulator loads it. Less tedious ;) )

P.S. make sure you put the opengl option back on in mednafen.cfg, much less CPU intensive than sdl)

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> It shouldn't remove any settings if you do it manually. If you are really worried, you can make a quick tarball of your .compiz folder.

What I use at before I run the emulator
```
metacity --replace &
```
then after
```
compiz --replace &
```

(Well I have it automated with a small zenity script, so I can just type a few letters of the game name, then double click the result, and the right emulator loads it. Less tedious ;) )

P.S. make sure you put the opengl option back on in mednafen.cfg, much less CPU intensive than sdl)
that's good to know.  I never knew that command; I would always go to visual effects and disable visual effects.

edit: anyways, disabling compiz did not work.. Time to move on to the BIOS... that I manually dumped from my own GBA... :---)

---

### Post by grossaffe on 2008-10-25
okay, now hypothetically, if one had a GBA BIOS binary, how would one set Mednafen to find it?

---

### Post by FranMichaels on 2008-10-25
Alright, hypothetically, after you have dumped your own bios, and named it, let's say... gba.bios, drop it to 
~/.mednafen/

---

### Post by grossaffe on 2008-10-25
> **FranMichaels said:**
> Alright, hypothetically, after you have dumped your own bios, and named it, let's say... gba.bios, drop it to 
~/.mednafen/

and how would one check and be sure that Mednafen is indeed reading/using the bios that the previously unspecified individual manually dumped from his or her own legally purchased Gameboy Advance?

---

### Post by grossaffe on 2008-10-26
bump for possibly fresh eyes.

ROMs do indeed work in emulators through WINE, so they aren't the problem.  I'm just lost as to what it could possibly be.

---

### Post by grossaffe on 2008-11-02
thought I'd give an update.  Still haven't found a native GBA emulator that works with that ROM.  But I booted into windows and downloaded and tried every single GBA emulator I could find (except the one I'm already running in WINE) and none of them ran the ROM either.  so is it possible that "no&gba" is the only GBA emulator written that can handle running it (although there are some graphics problems even in that one, which is why I bothered to continue my quest to find a more perfect emulator).

Odd that there's only one emulator in the entirety of the internet that can seem to handle the game.

---

### Post by golem1989 on 2008-11-02
i got the same problem... only no&gba works with wine. nothing else...
i don't care, if it's running via wine or not. but i can't link 2 emulators with no&gba and that's a real problem for my pokemons, which want to develop due to pokemon-trading^^

---

### Post by grossaffe on 2008-11-02
> **golem1989 said:**
> i got the same problem... only no&gba works with wine. nothing else...
i don't care, if it's running via wine or not. but i can't link 2 emulators with no&gba and that's a real problem for my pokemons, which want to develop due to pokemon-trading^^

I haven't tried trading because I haven't found out how to get two different games going at once.  I can have two instances of one game, but I can't get two different games.

I really am curious as to what the problem could be, though.

---

### Post by Karilex on 2008-11-03
The only gba emulator that works with me on ubuntu is the no$gba it can also emulate nds games so it's basically two birds with one stone unfotunately you may find that not being able to resize your screen is pretty anoying but if you're willing to try it here's the link http://en.utilidades-utiles.com/download-no$gba.html
Just download the windows xp version hope that helps

---

### Post by Karilex on 2008-11-03
oops sorry i hadn't read what people posted before and hadn't seen how everybody knew about that anyway there was an old gba emulator that worked on ubuntu unfortunately it was even worst than no$gba and i can't find the download link anymore guess i'll tell you if i find a good emulator

---

### Post by grossaffe on 2008-11-03
update: I read that apparently VBA 1.7.2 does not work with this game.  I've downloaded the windows version of 1.6 and run it in vista and the ROM does work in that.  I will update when I try a linux version of VBA 1.6 and if that doesn't work I'll try to run in WINE.

for those interested, VBA 1.6 for windows: [http://www.ngemu.com/gba/vba.php?action=download&req=emu&id=237](http://www.ngemu.com/gba/vba.php?action=download&req=emu&id=237)

---

### Post by MasterNetra on 2008-11-03
I'm using "visualboyadvance" from repository and it works perfectly for me. Not sure if its in Intrepid/Hardy 's default repository sense I did enable Medibuntu's repository prior to searching. And VBA even plays GBC games. Not nds though.

---

### Post by grossaffe on 2008-11-03
> **MasterNetra said:**
> I'm using "visualboyadvance" from repository and it works perfectly for me. Not sure if its in Intrepid/Hardy 's default repository sense I did enable Medibuntu's repository prior to searching.

what games are you playing on it?

---

### Post by MasterNetra on 2008-11-03
> **grossaffe said:**
> what games are you playing on it?

I'm into the pokemon games mostly. Pokemon Leaf Green atm. Its a pretty nice re-make of red & blue with Gold/Silver stuff added to some degree.

---

### Post by grossaffe on 2008-11-03
> **MasterNetra said:**
> I'm into the pokemon games mostly. Pokemon Leaf Green atm. Its a pretty nice re-make of red & blue with Gold/Silver stuff added to some degree.

how about Emerald/Ruby?

---

### Post by grossaffe on 2008-11-03
okay guys, I'm trying to compile VBA 1.6 from source but I'm coming up with an error during the ./configure stage:
```
 ./configure
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable GP32 emulation... (cached) no
checking whether to enable C core... (cached) yes
checking whether to enable development features... (cached) yes
checking whether to use mmx... (cached) no
checking whether to enable profiling... (cached) yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for bison... no
checking for byacc... no
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
./configure: 1313: flex: not found
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: 1: lex: not found
configure: error: cannot find output from lex; giving up

```

any tips?

---

### Post by MasterNetra on 2008-11-04
> **grossaffe said:**
> how about Emerald/Ruby? Yea it runs those just fine. And don't compile from source. I got it straight from rep, no compiling at all. if you can't find "visualboyadvance" (minus "" of course) in repo then enable medibuntu's repo.

---

### Post by grossaffe on 2008-11-04
> **MasterNetra said:**
> Yea it runs those just fine. And don't compile from source. I got it straight from rep, no compiling at all. if you can't find "visualboyadvance" (minus "" of course) in repo then enable medibuntu's repo.

it doesn't work.  already tried every variation of emulator out there.

---

### Post by MasterNetra on 2008-11-04
You using Ubuntu 8.04 or the new 8.10?

---

### Post by grossaffe on 2008-11-04
> **MasterNetra said:**
> You using Ubuntu 8.04 or the new 8.10?

8.04 64-bit

---

### Post by Grishka on 2008-11-04
> **grossaffe said:**
> okay guys, I'm trying to compile VBA 1.6 from source but I'm coming up with an error during the ./configure stage:
```
 ./configure
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable GP32 emulation... (cached) no
checking whether to enable C core... (cached) yes
checking whether to enable development features... (cached) yes
checking whether to use mmx... (cached) no
checking whether to enable profiling... (cached) yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for bison... no
checking for byacc... no
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
./configure: 1313: flex: not found
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: 1: lex: not found
configure: error: cannot find output from lex; giving up

```

any tips?

[apt://flex]("apt://flex")

---

### Post by grossaffe on 2008-11-04
> **Grishka said:**
> [apt://flex]("apt://flex")

alright, that got me further.  next error: (not gonna post the whole redundant code)
```
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.

```

looks like something to do with C++ and gcc, but I couldn't find anything in synaptec that stood out as being the package I need.

---

### Post by Grishka on 2008-11-04
> **grossaffe said:**
> alright, that got me further.  next error: (not gonna post the whole redundant code)
```
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.

```

looks like something to do with C++ and gcc, but I couldn't find anything in synaptec that stood out as being the package I need.

what's your compiler version? are you on a 64-bit system? you might want to try installing the gcc and g++ multilib packages.

---

### Post by grossaffe on 2008-11-05
> **Grishka said:**
> what's your compiler version? are you on a 64-bit system? you might want to try installing the gcc and g++ multilib packages.

running 64-bit.  Just install gcc 4.2 multilib and g++ 4.3 multilib and those did not do the trick.

---

### Post by Grishka on 2008-11-05
> **grossaffe said:**
> running 64-bit.  Just install gcc 4.2 multilib and g++ 4.3 multilib and those did not do the trick.

I'd think you should use the same versions of gcc and g++. where did you get the source from?

---

### Post by grossaffe on 2008-11-05
> **Grishka said:**
> I'd think you should use the same versions of gcc and g++. where did you get the source from?

typo, it was 4.2 for both.

as for the source, I got it from... well I don't remember.  I was searching around for a place that had 1.6 for linux.  I'll see if I can find it.

---

