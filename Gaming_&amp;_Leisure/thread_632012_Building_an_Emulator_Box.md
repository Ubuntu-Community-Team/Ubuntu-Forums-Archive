---
title: "Building an Emulator Box"
date: 2007-12-05
forum: Gaming &amp; Leisure
---

### Post by zykhou on 2007-12-05
I've recently gotten inspired to work on a project. I'm taking a decent desktop computer (new parts from about 2-3 years ago), and making a full scale emulator box out of it. My plan is to have a simple set up so that I can play all my favorite games from the dawn of gaming up to the PSX/N64 Era on one machine.

For the controllers, I want to use USB/Controller Convertors so that I can use the original controllers. I've found such a device for Playstation controllers, but do such exists for other systems? The primary systems I want to emulate are the NES, SNES, Genesis, Playstation, and N64. I'd much prefer using the actual controllers as opposed to some 3rd party joystick (takes away from the charm IMO). Does anyone know sites that sell such devices? If not, is there a way to hack one up?

On a similar note, I've done a decent bit of emulation, but most of it used to be on a windows box, what emulators do you recommend using in linux? [NES, SNES, Genesis, Playstation, N64 Mainly]

---

### Post by desertboy on 2007-12-05
I'd highly recommend using windows on ths box as the wealth of emulators is far better in windows than linux.

If you want to use linux PSX you're spoilt for choice, EPSXE, PCSX & PSX all work well. 

For N64 Mupen seems to be the only game in town.

---

### Post by NightCrawler03X on 2007-12-05
PS/PS2 - Smartjoy Plus
SNES - Super Smartjoy

I'm not sure about other systems.
But you can go to
[http://fantasyanime.com/emuhelp/emuhelp_05.htm](http://fantasyanime.com/emuhelp/emuhelp_05.htm)
for more details

---

### Post by Steveway on 2007-12-05
If you want a box only for this task then I would setup Mythtv.
You can use it as a frontend to select the games from your collection, looks good and it is easy to control.
I use that for my Snes and Genesis (Sega Megadrive) games.
For Snes I would recommend Zsnes, it's the best emulator so far for it.
i'm using Gens for Genesis, there is a .deb somewhere here on the board.
PCSX for your playstation games.
Mupen for N64 (though I have no experience with N64-emulation on a Pc, I rather use my console for that.)
I'm not playing NES games on the Pc but I do have GFCE installed, maybe someone different knows what the best choice for that would be.
I'm gonna buy one old small Pc soon for that task, too.

---

### Post by acoustibop on 2007-12-05
I know there are also adapters for the N64 controller as well, although I'm not sure who makes them.  You may not be so lucky with the older controllers; even if they used to be made, I doubt there's enough of a market any more to keep them in production.

As far as emulators are are concerned, I'd recommend:

Nintendo:
FCEUltra for the Nintendo Entertainment System (in the repositories)
ZSNES for the SuperNES/Super Famicon (in the repositories; v1.43 for Feisty, 1.51 for Gutsy)
[Mupen64]("http://mupen64.emulation64.com/") for the Nintendo 64 - I've had it running, but never brilliantly.  Should be Ok with a higher end box and a bit of setting up, I should think.

Sega:
Master System: none (woe!)
Genesis/Megadrive: [GENS]("http://ubuntuforums.org/showthread.php?t=290008")

Sony:
Playstation: definitely [pSX]("http://psxemulator.gazaxian.com/"): [ePSXe]("http://www.epsxe.com/") and PCSX (in the repositories) are for more hassle and don't work as well.  Also, ePSXe and PCSX are about enhancement, while pSX is about accurate emulation: for an authentic Playstation experience, it's must-have.
Playstation 2: [PCSX2]("http://www.pcsx2.net/"), but you'll need a really high end box for any sort of results.

Most of these these emulators run excellently in Ubuntu: Mupen64 will need a fairly high end box and PCSX2 a very high end one.  The latest (2.13) GENS debs in the thread I pointed to don't work for everyone; if they don't work for you, try the 2.12b one (also in that thread).  FCEUltra and ZSNES work excellently, and I'm beginning to think pSX actually works better in Ubuntu than in Windows. ;)

---

### Post by NightCrawler03X on 2007-12-06
> Master System: none (woe!)
[Dega](http://www.emulinks.de/emus/dega-1.12.tar.gz)

---

### Post by acoustibop on 2007-12-06
Nice one, NightCrawler03X - will have give it a whirl! ;)

---

### Post by Sockerdrickan on 2007-12-06
I recommend emulators from [www.tuxemu.se.nu](www.tuxemu.se.nu) because they are mine lol.

---

### Post by mellowd on 2007-12-06
You can pick up a lot of controller converters on ebay.

---

### Post by FranMichaels on 2007-12-06
> **NightCrawler03X said:**
> [Dega](http://www.emulinks.de/emus/dega-1.12.tar.gz)

Although not stated explicitly on the page, [mednafen]("http://mednafen.sourceforge.net/") does support sms/gg as well.

In addition, "The Atari Lynx, GameBoy (Color), GameBoy Advance, NES, PC Engine(TurboGrafx 16), SuperGrafx, Neo Geo Pocket (Color), PC-FX, and WonderSwan (Color) are emulated." I highly recommend it. :)

---

### Post by Dimitriid on 2007-12-06
Enough good tips on the box already, but a personal question: Why leave the gameboy behind? imho my favorite emulator by far on my current desktop its VisualBoyAdvance. The gba has just tons and tons of games you should try, some that are not available to other consoles at all ( ie. two of my favorites, Metroid Fusion and Metroid Zero Mission ) or remakes/improvements from nes and snes that are way better and improved on it ( ie Final Fantasy I&II dawn of souls, Final Fantasy V advance, etc. )

---

### Post by valkarin on 2007-12-08
I didn't see my favorite Nintendo emulator up there.  iNES.  It is the best I have used thus far.  You should also get stella and compile it yourself instead of using the version in the repos so that you can have a GUI for it.  You might also look into MESS if you are adventurous.  I can't get it to work right, but that may be my lack of skills;)

---

### Post by gcrussell1 on 2007-12-09
> **acoustibop said:**
> 
[Mupen64]("http://mupen64.emulation64.com/") for the Nintendo 64 - I've had it running, but never brilliantly.  Should be Ok with a higher end box and a bit of setting up, I should think.

...

Mupen64 will need a fairly high end box

Mupen64 is pretty good, not as good as Project64 or 1964, but they're both Win specific. So far, I've only had one problem with it that really affects playability of any games, and that would be that the Lens of Truth doesn't work in Zelda: Majora's Mask, but I think that's a plugin issue anyway - the Open GL plugins for N64 are unfortunately not quite up to the level of some of the D3D ones as far as I've seen.

However, as for it's needing a fairly high-end box, don't be too frightened by that - I'm running Mupen64 excellently (if not at huge resolution) with a pretty old laptop with a P4 3 Ghz, Radeon Mobility 9600, and 768 MB DDR Ram - not a particularly impressive build these days, so if you can match that, you'll be perfectly fine for Mupen64. It's really a pretty nice project, it's just a shame that there aren't more people lending a hand to its development.

---

### Post by acoustibop on 2007-12-09
I'll have to give it another go then, gcrussell1.

---

### Post by gcrussell1 on 2007-12-10
> **acoustibop said:**
> I'll have to give it another go then, gcrussell1.

If you give it a run, I recommend that you try out the plugin you can find here: [http://www.emutalk.net/showthread.php?t=37658&page=12](http://www.emutalk.net/showthread.php?t=37658&page=12) 

It's working pretty well for me, though I still need to tweak the settings a bit to get decals working well. When you compile the new Glide64 plugin, you'll just put the .so file in the plugins folder, regardless of the instructions in the makefile, the compiler doesn't make a .ini file, but the one that comes prepackaged with the version of Glide64 in the Mupen64 0.5 tarball seems to work fine for it. Be sure to check the boxes in the Glide Wrapper section of the config menu for it though, unless you're running a Voodoo card (and I seriously doubt you are... since Voodoo's been defunct for several years now), since the wrapper addons are needed to make OpenGL run the plugin properly.

Now if only my gamepad's joystick worked as well as the original controller... as it is, I'm stuck with gross motor skills ala the GameCube ports of Ocarina of Time and Majora's Mask... not unplayable, but a long sight harder than it needs to be.

---

### Post by acoustibop on 2007-12-10
Ta, I'll try that, gcrussell1.  BTW I think there are adapters for using an N64 controller with a PC.  Adaptoid is the one that springs to mind.

---

### Post by inversekinetix on 2007-12-10
id recommend using a stripped down windows XP box for your emulator, maybe running maximus arcade for your front end.  have a look on youtube for what it is.

maximus arcade

you should also get some monster harddrives, I have about 3TB of roms now and theres still so many more to get

---

### Post by gcrussell1 on 2007-12-10
> **acoustibop said:**
> Ta, I'll try that, gcrussell1.  BTW I think there are adapters for using an N64 controller with a PC.  Adaptoid is the one that springs to mind.

Yeah, I'm gonna give that a try when I get back to the States next month... unfortunately I don't think I've got a ton of easy access to Adaptoid stuff or even an N64 controller here in Jingzhou, I doubt there are more than a couple hundred people in the whole city who have ever even owned an N64 really...

---

