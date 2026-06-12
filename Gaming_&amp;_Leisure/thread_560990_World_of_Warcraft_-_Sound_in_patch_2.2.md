---
title: "World of Warcraft - Sound in patch 2.2"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by nerfbat on 2007-09-27
Hi,

I've been happily running WoW with wine, but of course bug day - sorry, patch day - has caught me out.

Since patch 2.2 (yesterday) I have no sound in the game (yes, it's enabled in Sound Options, and SetSoundSystem "1" or whatever the setting it in Config.wtf -- it was working until the patch).

I have winecfg set - I think - to OSS, and I use aoss so I can use Ventrilo (also under Wine) at the same time.  (I was looking forward to in-game voice chat to be able to stop running vent, now I'm just hoping my guild don't switch to it or I won't be able to raid.)

I tried setting hardware acceleration in winecfg to 'Basic' - similar to the wow tech support forums recommending that's done in 'dxdiag'.

Anyone have any further ideas about how to fix this?  Log file below, FWIW.

Cheers,


$ cat SESound.log
9/26 17:14:18.307 => Setting up Game Sound:
9/26 17:14:18.328 - SESound Engine Init
9/26 17:14:18.328 - FMOD Memory Init
9/26 17:14:18.329 - FMOD System Create
9/26 17:14:18.330 - FMOD version 00040725 detected
9/26 17:14:18.331 - 1 Output drivers detected
9/26 17:14:18.332 --- [0] alsa-oss
9/26 17:14:18.333 - Using [0] alsa-oss for Game Output
9/26 17:14:18.333 - Using 12 channels.
9/26 17:14:18.359 ######## FMOD ERROR! (err 59) Error initializing output device.
9/26 17:14:18.359 .\SoundEngine.cpp(1783)
9/26 17:14:18.359 ######## FMOD ERROR! (err 59) Error initializing output device.
9/26 17:14:18.359 ######## FATAL ERROR INITIALIZING. ALL GAME SOUND DISABLED.
9/26 17:14:18.359 .\SoundEngine.cpp(1784)
9/26 17:14:18.359 => Game Sound Init Failed.

---

### Post by Faud on 2007-09-27
Did you try updating to the newest version of wine ?

---

### Post by hikaricore on 2007-09-27
Blizzard replaced their once powerful hardware accelerated sound system with a chite software sound system.
There are a few threads around with suggestions here and on the WoW forums.

Sorry it's late or I'd dig for them.  *tired*

---

### Post by Faud on 2007-09-27
Sorry I was tired too...so to expand on the other forums: winecfg, then audio, change to emulation and then click the box that says driver emulation.
You may have to change your sound buffer in your config.wtf
( I personally did not end up having to do this )

Happy game time.  Im crashing. See yall tomorrow.

---

### Post by nerfbat on 2007-09-27
I'm using whatever the latest Wine is in Ubuntu.  I could download a non-distro one if that helps. 

I know I fiddled with a few settings in winecfg, but I can't remember exactly what, so I'll give those things a go tonight.

---

### Post by nerfbat on 2007-09-27
So, I'm on wine-0.9.33.

Changing things to use Alsa makes.. well, I won't say it makes the sound work, although it does make noise happen.  

I've got it set to 'Emulation', 'Driver Emulation' is checked; Rate is 48000 and BPS is 16.

The sound now plays, but it crackles, jumps, varies wildly between high and low.  I've twiddled the SoundBufferSize to no avail.

---

### Post by nerfbat on 2007-09-27
wine-0.9.45 improves things, and it sometimes seems to be working, but then the sound starts stuttering.  Combat makes it particularly bad, nice quiet areas are somewhat better.

I've changed to
SET SoundOutputSystem "2"
and continued twiddling the buffer size but it doesn't seem to make any difference.

My sound card is


00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

---

### Post by hikaricore on 2007-09-27
There is also speculation that SoundBufferSize no longer works the way it used to if at all.

I believe it still works, but I'm not convinced it works well.

---

### Post by snackrifice on 2007-09-27
in the terminal type winecfg and select wow profile from the application tab, if its not there make one for it. go to audio. uncheck OSS and check ASLA fixed it for me.

---

### Post by Confuzius on 2007-09-27
Same deal for me, my best solution so far is to turn off alsa and oss all together just so I can have a half decent framerate. (which is still almost half of what it was pre-2.2)

I have tried every combination of alsa/oss and all of the hardware acceleration/emulation options and havn't found a suitable option.

Running onboard realtek97 generic (can't remember 100% not home now)

I'm actually getting tempted to get out my vista CD :(

Off topic, has anyone had any luck running WoW on a virtual machine? or would that be way too slow?

---

### Post by nerfbat on 2007-09-27
I have Alsa checked, and OSS unchecked, already.

---

### Post by derekr44 on 2007-09-27
So it isn't just me.  Sound has been crappy since the patch.  I'm running it in Crossover and it skips pretty bad.  Looks like if it's run by a software driver, then I'll have to scale it way back to low qual.

---

### Post by American_Outcast on 2007-09-27
I am using  WoW with CrossOver. I am noticing there is more background "static" but the sound itself does work. It just instant working that great, especially when I am in Outland for some reason.

---

### Post by Despedezador on 2007-09-27
I had sound problems also with 2.2 on world of warcraft, but i managed to get rid of the problem.  Here is what i did.

1) went into the Config.wtf file, and typed in SoundOutputSystem "1" (did this before, but for some reason it was missing)

2) went into winecfg from the terminal, and went to the audio section.  Then, i changed the Hardware acceleration to Emulation, and clicked the box for Driver Emulation.

This solution has worked well for me... hope it does for you all too.

---

### Post by LauraSakura on 2007-09-27
people on OSX and windows are complaining on the WoW forums about it as well, a lot of people are having sound issues now :( It's not just a Wine issue.

---

### Post by nerfbat on 2007-09-28
Er, I'm sure I replied to this last night  Oh, I did.  It's too early for me.

I already have OSS unchecked and ASLA  checked.

---

### Post by nesty on 2007-09-29
My sound is buggin out too.   The best solution I've had is to run it with ALSA, set my winecfg to full, and increase the rate on my sound.  It's still choppy, but it's better than any other combination I've found.

---

### Post by keeper-of-the-real on 2007-09-29
AS a previous poster stated, Windows users are having this problem too.  

I thought I fixed my issues a day ago, after 4 hours straight and no problems.  For some reason it returned today.

So, I booted up Vista, which is supposed to be my DVR machine only and loaded Wow.  

I don't have ANY  WOW  sound in Vista at all.  

I'll take choppy sound in ubuntu for the time being.  I'm sure Blizzard is in a tizzy over this if so many are having issues..:confused:

---

### Post by Seraed on 2007-09-29
Just upgraded Wine to 0.9.46, set to emulation and enabled driver emulation. Also set SoundOutputSystem to 2 (was 1). Everything is working great again, no stuttering, and my frame rates are just as they were pre-patch.

Now if only the small time addon authors get to work releasing up to date mods I'd be set.

I'm happy to not have to rely on Cedega again :P

---

### Post by Faud on 2007-09-29
Which drivers are you using Seraed ?

---

### Post by Seraed on 2007-09-29
> **Faud said:**
> Which drivers are you using Seraed ?

For sound? Using Alsa.

---

### Post by Power_Nisse on 2007-09-30
> **snackrifice said:**
> in the terminal type winecfg and select wow profile from the application tab, if its not there make one for it. go to audio. uncheck OSS and check ASLA fixed it for me.


/bow..

Works like a charm. thank you =)

---

