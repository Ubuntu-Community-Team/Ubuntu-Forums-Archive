---
title: "SDLMame- Sega games sound distorts"
date: 2008-12-10
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-12-10
Hello all,

I have noticed that my audio distorts when I play Sega games with SDLMame.

I have a Pentium 2.8ghz machine with 2gig ram and 256meg ram video.  Clearly this machine should be able to run games from the 80's fine.  I ran games from 1998 fine on my machine without any audio problems.  For the most part Sega games are the only ones I have skipping/distortion in the audio.

I have tried four Sega games and they all have the same problem:

Hang On
Outrun
Space Harrier
After Burner

The video plays fine and is fairly smooth, just the audio is choppy.  Games from the same era work fine.

Any assistance would be much appreciated.

EDIT 12-10-08

Tonight I went back into Windows and tested the games listed above with Mame under Windows.  I DO NOT have the audio problem there.  The Sega games all run fine.

I also did some additional research in regarding the later versions of Mame.  SDLMame 0.123 is based on MameUI 0.123 (Windows).   Supposedly after the version of Mame 0.107, performance took a nosedive.   I did have version 0.123 and I didn't like the performance I was getting with vector games.  I never bothered to try those Sega games on it because I reverted back to version 0.100 of Mame, which I get overall much better performance from.

Supposedly SDLMame goes as far back as version 0.111, which falls into the later version category.  

However, even when using identical versions; Mame UI 0.123 and SDLMame 0.123, performance was MUCH better overall in Windows.

So as of now I don't know what else is causing the issue, but I am thinking that I want to try the Windows versions of Mame running in Ubuntu through Wine.  I am not sure if it will even work.  Already I hit an obstacle in that I don't know how to run a command line instruction when using Mame in Wine.  Normally you would just click the executable, but with Mame you need to launch the executable WITH the rom.  That I don't know how to do yet here in Linux.

But I do know that with SDLMame you CAN go into the terminal and just type "Mame (Whatever rom you want to run)" and enter.

So that is going to be the next step to try Windows Mame out in Wine.

Geo

---

### Post by Sockerdrickan on 2008-12-10
SDL Pulseaudio bug

---

### Post by jukingeo on 2008-12-10
> **Tux0r said:**
> SDL Pulseaudio bug

As far as I know, I am only using ALSA for audio on my Ubuntu Studio installation.  I am not using OSS/Pulse.

Geo

---

