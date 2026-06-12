---
title: "Console emulation?"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by darkmage77 on 2007-07-23
I've been using Ubuntu off and on for about a month now, and so far I'm liking it (minus my video still not working quite right, but that's for another post :). In fact, there's one thing that's keeping me from kicking M$ off my comp, and that's games. But it's not the games you think.

One of my passions since getting my first computer in 1998 is console emulation. I've gotten quite a refined library of games I like to play, and found the emulators that work the best for me. But in Linux I'm running into a problem of utilizing the emulators I've found so far.

A lot of the emulators are command-line, and while I'm usually not picky, I prefer GUI at least for these since I can select games w/o having to open Nautilus. So any frontends for particular emulators are welcome as well.  If anyone can help, that'd be awesome.

Here's a list of the systems I have games for, and emulators I use in Windows:

Atari 2600 (PC Atari)
NES (FCE Ultra)
SNES (ZSNES/bsnes)
Gameboy/Advance (VBA)
Master System (Meka)
Genesis (GENS)
Arcade (using MAME32 on Windows)
PC Engine (MagicEngine)
PSX (ePSXe)

Thanks!

---

### Post by ddrichardson on 2007-07-23
snes9x is in the repository as is zsnes, mame, xmame, visualboy advance.

If you use synaptic, search "emulator" - there's quite a few

---

### Post by F-3582 on 2007-07-31
You should definitely give [Mednafen]("http://mednafen.sf.net") a try. The latest version has GBA, GB, NES, PC-Engine, Atari Lynx and WonderSwan support. Although it is command-line only, there's a good deal of stuff you can configure in runtime. Just make Gnome open the desired files with Mednafen and that's it. However, the version in the repos is a bit outdated, so get the source, type "sudo apt-get build-dep mednafen" and compile/install this thing as usual.

For Genesis emulation I use [Gens]("http://ubuntuforums.org/showthread.php?t=290008") which has a pretty irritating GUI (check the OSD instead if you wanna know which option has been set), but in the end it works.

For Snes emulation I use Zsnes, although its SA-1 emulation is pretty buggy. Unfortunately Snes9x has sound issues on my computer.

Arcade-wise I go with [SDLMame]("http://rbelmont.mameworld.info/?page_id=163"). I read that it even has a built-in ROM browser GUI, now.

Meka has been released for Linux, too, but it always locks up my Xsession for some reason.

ePSXe and Pete's plugins are available for Linux as well. pSX has been out for Linux, too.

Mupen64 (guess what for) is a pretty solid Linux emulator.

That pretty much covers the stuff I use.

---

### Post by wana10 on 2007-07-31
instead of epsxe i use pSX

and for sdlmame you can get the deb [here](http://wallyweek.altervista.org/).

---

### Post by Nythain on 2007-07-31
almost all of those have a linux port... here's what i currently use

nes - i dont have a linux emu yet, havent wanted to play any of my games
gba - vba (though i refuse to play gba games on my linux box due to teh lack of cheat code/rom hacking support in the linux port of vba)
sms - mekanix
sega gg - mekanix
genesis - gens
snes - zsnes

currently looking for a decent turbografx 16 emulator for linux, but i havent started searching yet... once i get a better machine i will get back into psx and ps2 emulation... but for now my lowly 2.0ghz 768meg ram box just wont suffice

---

### Post by DoktorSeven on 2007-08-01
2600 - Stella
NES - FCEU
SNES - ZSNES
GB/GBA - Mednafen
TG16/TCD - Mednafen
Genesis/Megadrive - Gens
Arcade - SDLMame
PS1 - ePSXe
N64 - Mupen64

---

### Post by DirtDawg on 2007-08-01
I used to use something called Stella for Atari 2600 emulation. It works great and it's in the repos.

There's no GUI, but it's pretty easy to run through the terminal:
```

cd /path/to/my/Atari/ROMs/

stella ROMNAME

```

Or something close to that. I haven't used it in several months. If that's not right, there's always
```
 man stella 
```

---

### Post by DoktorSeven on 2007-08-01
> **DirtDawg said:**
> I used to use something called Stella for Atari 2600 emulation. It works great and it's in the repos.

There's no GUI, but it's pretty easy to run through the terminal:


Actually, latest versions of Stella have a self-contained GUI in a window.

---

### Post by DirtDawg on 2007-08-01
> **DoktorSeven said:**
> Actually, latest versions of Stella have a self-contained GUI in a window.

That's cool. I also noticed you posted Stella already! I'm slow on the draw.

---

### Post by Incense on 2007-08-01
How does SDLMame work? I have only used KXMame, and while it worked, iI felt like it could be better.

I would add DOSBOX to your list. Works great!

---

### Post by F-3582 on 2007-08-01
> **Incense said:**
> How does SDLMame work? I have only used KXMame, and while it worked, iI felt like it could be better.

I would add DOSBOX to your list. Works great!
I didn't try that new feature in MAME. In the past I always used QMC2. Go to [http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=30690&page=0&fpart=1](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=30690&page=0&fpart=1) and download the deb in the first post, cuz the later version breaks the configuration stuff apart.

---

### Post by DoktorSeven on 2007-08-01
> **Incense said:**
> How does SDLMame work? I have only used KXMame, and while it worked, iI felt like it could be better.

I would add DOSBOX to your list. Works great!

SDLMame has an internal menu system to select games from (from the default ROM directory set in the .ini) if you run it without specifying a specific ROM.  It's pretty slick, though not as versatile as a real frontend like kxmame.

---

### Post by Nythain on 2007-08-01
> **DoktorSeven said:**
> 2600 - Stella
NES - FCEU
SNES - ZSNES
GB/GBA - Mednafen
TG16/TCD - Mednafen
Genesis/Megadrive - Gens
Arcade - SDLMame
PS1 - ePSXe
N64 - Mupen64
thanks for the introduction to mednafen... installing now... looks pretty groovy

---

### Post by acoustibop on 2007-08-01
I'm using pSX and ePSXe for playstation (pSX almost entirely), ZSNES for Super Nintendo, GENS for Genesis, Mega CD etc and Mupen64 for Nintendo 64.

I've just installed FCEU for NES and am just figuring out configuring my controller.  I'd love to find a good, working emulator fot the Master System.

---

### Post by MWilliams13 on 2007-08-01
its not on your list but try Project64 with Wine. I downloaded project64 and it opens the rom list fine but have not gotton around to playing any. It is a N64 emu but is still  fun

---

### Post by BigSilly on 2007-08-02
Project64 doesn't work under WINE, at least it didn't for me. It kept complaining that I hadn't set the plug-ins properly, even though I most certainly had.

---

### Post by Sockerdrickan on 2007-08-03
Very compatible GB/C emu for the serious player
[http://ubuntuforums.org/showthread.php?t=516254](http://ubuntuforums.org/showthread.php?t=516254)

---

### Post by DoktorSeven on 2007-08-03
I have gotten PJ64 running under Wine but it's very choppy and crashes a lot.  I'd stick with Mupen64.

---

### Post by BigSilly on 2007-08-03
Mupen 64 is pretty neat, and I use it a lot. I can't help but wish they'd keep working on it and bring us an update. It's a couple of years old now, and definitely due some love. Another update and it'd remove the wish for Project64 on Linux surely.

---

### Post by Sockerdrickan on 2007-08-03
Yeah I want better sound and fps (17fps i OoT, watch my sig)

---

### Post by F-3582 on 2007-08-03
> **Tux0r said:**
> Yeah I want better sound and fps (17fps i OoT, watch my sig)
Maybe your config is messed up.

---

### Post by Sockerdrickan on 2007-08-03
Ok I'll check on that

---

### Post by BigSilly on 2007-08-03
> **Tux0r said:**
> Yeah I want better sound and fps (17fps i OoT, watch my sig)

I do a bit better than that on Ocarina! 17 fps?? Definitely check your plugin configs.

The main issue for me with Mupen64 is the sound and the general compatibility. I can tinker with the audio config text file, and get fairly decent results thanks to some advice from the official forum, but the sound still lags somewhat. Also, there are many games that no matter what you do you cannot get them to run. 

So I'd love to see an update for Mupen. What do you think the chances are of this? Anyone here close to the guys who work on it?

---

### Post by Sockerdrickan on 2007-08-03
actually I think it's smoother but it says 17 FPS (running Hacktarux ported gfx plugin)

---

