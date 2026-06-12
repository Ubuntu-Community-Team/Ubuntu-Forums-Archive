---
title: "NES games on Debian(Ubuntu)"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by kunkman93 on 2008-01-13
Yo.This is my first time really using Linux but i need to know how to play NES games on my computer. Thanks Alot!!!! Also the code.

---

### Post by dgray_from_dc on 2008-01-13
Go into synaptic, and search for emulators.  You should see some of the popular ones used in windows and a few more obscure ones unique to Linux.  Right click on them to install.  If you don't see any of them, then you may have to enable the universe and/or multiverse repositories.  Then repeat your search.

---

### Post by xpod on 2008-01-13
I tried playing some of my girls DS games yesterday,all to no avail.
Desume was what i tried on but it was having none of it,on either pc here.
i`m sure theres also apps for your nes thingy though.

Good luck with Linux either way.
I think the games are best kept to the consoles & hand held thingys anyway.....thankfully.
I just got sick of my 2 older girls refusing their younger sister a shot of the DS`s  yesterday so thought i`d try get the games working on a pc for her.
I`m buying her one next week now and regret not having thought her old enough in the first place......she`s 7 and been using Puppy Linux for over a year and i deemed her too young for a silly DS......doh.](*,)

She had long since got her hands on one of  the DS`s by time i was finished trying with Desume though so it was neither here nor there.

---

### Post by DoktorSeven on 2008-01-13
The latest versions of Ubuntu have FCEU and GFCEU, which is an excellent NES emulator and an excellent GUI frontend to FCEU (since FCEU is commandline only; GFCEU makes it where you don't have to mess around with the commandline to run it).  

Both are in Universe, so search for how to enable (and update when you do) the Universe repository if you haven't already, and install from Synaptic the above packages (or just do **sudo apt-get install gfceu fceu** from a terminal prompt).

As for a DS emulator, the NDS is still very new and emulation hasn't really progressed too much -- there's a couple of decent NDS emulators on Windows, but I understand they're still far from perfect.  Possibly using Wine to run one of those might be a decent choice there.  I don't really do emulation of modern consoles/handhelds anyway...

---

### Post by homerhomer on 2008-01-14
by far the best way is with [http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

use synaptic or apt-get install mednafen to install it

---

### Post by harmsc12 on 2009-08-08
How do you use the game genie feature this supposedly has?

---

### Post by DeadSuperHero on 2009-08-09
Although you're looking specifically for NES emulators, a great SuperNintendo emulator I love using is ZSNES. You can find it in Synaptic.

---

### Post by homerhomer on 2009-08-09
Honestly not trying to do the 1up thing. But this version of snes9 with gtk gui support works great for me 
[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)


some dude on youtube describing some emus - [http://www.youtube.com/watch?v=8sxQJdmoEa4](http://www.youtube.com/watch?v=8sxQJdmoEa4)

---

### Post by disturbedite on 2009-08-09
best NES emulator imo is Nestopia (most accurate {realistic} NES emulator - not opinion).

---

### Post by mjkerpan on 2009-08-10
> **disturbedite said:**
> best NES emulator imo is Nestopia (most accurate {realistic} NES emulator - not opinion).
There's an ongoing feud between Nestopia and FCEU fans over that point. Both claim that their favorite emulator is more accuarate and can point to "ours emulates glitch X in game Y better than yours", but given that both play just about 100% of NES and Famicom games with few or no glitches, it's really a moot point.

I do tend to use Nestopia more as it has a better UI under Linux.

---

