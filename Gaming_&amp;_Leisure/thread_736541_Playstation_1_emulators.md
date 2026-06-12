---
title: "Playstation 1 emulators"
date: 2008-03-26
forum: Gaming &amp; Leisure
---

### Post by BetterSense on 2008-03-26
I've installed pSX. It works fine on my desktop but doesn't work properly on my eeePC. It skips and chops and eventually dies. Console output includes the line

```
(pSX:5898): GdkGLExt-WARNING **: Cannot open \x88P\x81\u0008L.so
```

I don't know much else to do to get it running. Any ideas?

---

### Post by acoustibop on 2008-03-26
A quick look on wikipedia suggests your EeePC may not be fast enough to run a Playstation emulator adequately, BetterSense; the fastest EeePC CPU is a 900 MHz Intel Celeron-M ULV 353, clocked at 630 MHz (70 MHz x 9).

What colour depth is your desktop set to?  It needs to be 32bit or, failing that, 16bit rather than 24bit.

---

### Post by BetterSense on 2008-03-26
Indeed, I think it's just the low system specs. Overclocking has allowed useable playback, but I'm not sure about heat buildup. I just got done swiss-cheesing my eeepc's case and bolstering the heatsinkage. I wonder if there are any lighter-weight PS1 emulators? SNES emulators?

---

### Post by Sockerdrickan on 2008-03-27
GameBoy games are lovely and playable over and over again.

---

### Post by cisforcojo on 2008-03-27
Agreed. Zelda - The Minish Cap is an incredible game. 
So are the Advance Wars games.

---

### Post by acoustibop on 2008-03-27
SNES emulators (ZNES - my favourite - or SNES9x) should be lighter weight than Playstation ones, BetterSense, but pSX is definitely the lightest weight Playstation emulator, particularly if you don't have a fast videocard you can shunt off some of the processing to.

---

### Post by FranMichaels on 2008-03-27
You can also give pcsx-df a try.

[http://aboenterprises.ca/pcsx-df/](http://aboenterprises.ca/pcsx-df/)

Releases should eventually end up here though
[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

---

### Post by basketcase421 on 2008-03-27
You should definetly be able to handle a SNES emulator.  I still use my old 133 mhz thinkpad for that.  Yes, I said 133 mhz... and it has 32 mb ram... woo hoo!!!

Even with the low specs of the eee, I would imagine with some tweaking, you could get a PSX emulator working, though, I am just guessing.  I used to play one on my Celeron 500 mhz desktop.  I can't remember which one it was, though.  I do know that it didn't do any special rendering, like AA and filter stuff, so that might be why it worked.  It wasn't exceptionally pretty, but it worked.

In the emulator you are using, have you tried PEOPs plugins?

EDIT: Nevermind... it doesn't look like pSX lets you use different plugins.  I am used to EPSXE on my Windows PC, that lets you use different gfx and sound plugins.  The PEOPs ones are easier on your PC, as they just do a direct emulation.  Vs something like a OpenGL or DX plugin that adds filtering and stuff (makes it look real purdy like...).  Does anyone know if EPSXE works on Linux?

---

### Post by BetterSense on 2008-03-27
I'm pretty sure it does. Maybe later, I'll try that with the plugins that make it easy on the computer. I'm not much interested in prettification, I just want to play FFT on the  go.

---

### Post by disturbedite on 2008-03-27
> **acoustibop said:**
> SNES emulators (ZNES - my favourite - or SNES9x) should be lighter weight than Playstation ones, BetterSense, but pSX is definitely the lightest weight Playstation emulator, particularly if you don't have a fast videocard you can shunt off some of the processing to.
agreed.  i don't recommend that ppl use snes9x when zsnes is clearly superior.  (at least in pure emulation).  same for playstation emulation; i don't recommend anything but pSX.

---

### Post by DoktorSeven on 2008-03-27
ePSXe has a software driver available, you might try it.  Heck, I still use ePSXe over pSX and I have 3d...

---

### Post by acoustibop on 2008-03-27
> **basketcase421 said:**
> ... I used to play one on my Celeron 500 mhz desktop.  I can't remember which one it was, though.  I do know that it didn't do any special rendering, like AA and filter stuff, so that might be why it worked.  It wasn't exceptionally pretty, but it worked... 

If that was within the last couple of years, it might have been pSX, basketcase421; if before that, most likely Connectix VGS.  VGS, along with Bleem! was a trailblazing Playstation emulator that, in some ways preceded pSX.  Until emulators like pSX and Xebra overtook it, it was reckoned to be the Playstation emulator with the best compatibility.  Unfortunately, it was Windows-only; AIR it was a very low resource emulator.

As far as SNES emulators go, my preference is ZSNES, but there have been some threads on the forum recently about a new modification of SNES9x.

---

### Post by basketcase421 on 2008-03-27
> **acoustibop said:**
> If that was within the last couple of years, it might have been pSX, basketcase421; if before that, most likely Connectix VGS.  VGS, along with Bleem! was a trailblazing Playstation emulator that, in some ways preceded pSX.  Until emulators like pSX and Xebra overtook it, it was reckoned to be the Playstation emulator with the best compatibility.  Unfortunately, it was Windows-only; AIR it was a very low resource emulator.

As far as SNES emulators go, my preference is ZSNES, but there have been some threads on the forum recently about a new modification of SNES9x.


Yeah!! That was it "Connectix".  Now, I have been using EPSXE in Windows, and I am very happy with it.  It has played every game I have tried, and using plugins makes every game look a lot better.

I prefer ZSNES too, but haven't tried Snes9xx for a long time.

---

### Post by mister_k81 on 2008-03-27
> **acoustibop said:**
> 

As far as SNES emulators go, my preference is ZSNES, but there have been some threads on the forum recently about a new modification of SNES9x.

Yes,  [SNES9x-gtk ](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703&postdays=0&postorder=asc&start=0), which has been around for a few months now, but it has been getting updated on a regular basis. Personally, I'm starting to prefer this one over ZSNES, because there are a few games that seem to be better emulated here.. For example, the sound has never worked properly for me in Earthworm Jim 2 under ZNES, but it works Great in SNES9x. Also, in Yoshi's Island on ZSNES, there are a few select areas where the graphics run out of sync for me (the areas with the get-dizzy puffball things) and make the level unplayable, but this hasn't been a problem in SNES9x-gtk.


As for Playstation Emulators... I use ePSXe on windows  but I could never get it to work on Ubuntu, so I use pSX instead. Which works well enough, as far as I'm concerned.

---

### Post by heartburnkid on 2008-03-27
Actually, Connectix started as Mac only.  And man, those were interesting times... I'd look at Macworld at the library, and all the tech pundits were talking about how, now that the Mac's gaming library had just gotten a huge shot in the arm via PS1 emulation, surely this would make the Mac into a powerhouse game platform and make developers take a second look...  Funny how that never happened and all.

---

### Post by acoustibop on 2008-03-27
Connectix VGS was, unfortunately, put out of business by Sony.  Sony took them to court over emulating their Playstation; the case was dismissed, but the costs to Connectix were steep enough to enable Sony to take them over - and then, of course, take the emulator off the market.  Since it was a commercial emulator, and only ever distributed as such, if you didn't buy a copy back then, it's actually illegal to use it now - although there are plenty of copies around on the internet.

Sony did something similar to Bleem! another commercial Playstation emulator.  This case was also dismissed, but the costs forced Bleem! to fold; Sony never acquired them, though.  I did buy a copy of Bleem! - ironic, because there's probably no company now to prevent people using Bleem! illegally, unlike with VGS, of which the right s are still owned by Sony.

---

### Post by BetterSense on 2008-10-28
Back from the dead, just in time for Halloween.

I sucessfully used pSX in the past, but now I gave gotten a different laptop, and it is not working. I do not understand the errors that it spits out. I tried using aoss and it didn't help.

```
chaz@singularity:/media/disk/emulators/pSX$ aoss ./pSX 
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
chaz@singularity:/media/disk/emulators/pSX$ 

```

---

