---
title: "Unreal Tournament GOTY sound quality issues"
date: 2007-01-01
forum: Gaming &amp; Leisure
---

### Post by NTolerance on 2007-01-01
I've got UT99 GOTY up and running, but the sound is horrible.  It pops, stutters, and skips.  I have sound working fine in Open Arena Quake 3, so something is up with UT.  I wonder if it has something to do with OpenAL sound.  

Here's my soundcard:

```
 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

I am running ALSA 1.0.14rc1.

---

### Post by neoclaw on 2007-01-03
Try installing "alsa-oss" and run UT GOTY like this: aoss ./ut

---

### Post by NTolerance on 2007-01-03
> **neoclaw said:**
> Try installing "alsa-oss" and run UT GOTY like this: aoss ./ut

Tried that, but it gave me garbled audio.  The executable I'm running is ut-bin.  Is that correct?

---

### Post by leech on 2007-01-03
I'm curious about this as well.  I tried to install Rune on Linux and it did the same thing, and it's based on the exact same engine as well.

Leech

---

### Post by diepruis on 2007-01-03
I have the same issue and almost the same audio controller

```
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
```

I've been trying to fix this for some time now, and I've been unsucessful. I've tried recompiling ALSA and even replaced some libraries.

I had the same issue with Neverwinter Nights though, and the solution for that was to copy the SDL / OpenAL libraries from /usr/lib over the libraries in the NWN directory. Maybe this can solve the UT issue?

---

### Post by NTolerance on 2007-01-03
> **diepruis said:**
> I have the same issue and almost the same audio controller

```
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
```

I've been trying to fix this for some time now, and I've been unsucessful. I've tried recompiling ALSA and even replaced some libraries.

I had the same issue with Neverwinter Nights though, and the solution for that was to copy the SDL / OpenAL libraries from /usr/lib over the libraries in the NWN directory. Maybe this can solve the UT issue?

I've updated the SDL lib to the latest version 1.2 used by UT2004.  This makes no difference.  I tried copying the stock Ubuntu OpenAL lib from the /usr/lib folder to the UT folder as well as openal.so from UT2004, but either of these will cause the game not to run.  :(

Supposedly there is a way to compile the latest OpenAL lib from here [http://www.openal.org/](http://www.openal.org/), but I don't end up with a .so file when I try to compile it.

---

### Post by NTolerance on 2007-01-04
I finally found my compiled libopenal.so file.  It was hidden in the src/.lib directory.  Unfortunately it causes UT not to start.  ](*,) 

Are you guys using the stock Edgy ALSA drivers or what?  I read somewhere that development releases of ALSA can cause problems with OpenAL.

---

### Post by munckfish on 2007-02-19
Hi

Dapper 6.06
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

I think I've got the same problem with both UT GOTY and UT 2004.

If I run ut directly I get no sound. If I run with esddsp I get strange warped half speed sound. If I run via aoss I get screeching noise.

Anyone got any further sorting this out?

---

### Post by diepruis on 2007-02-19
I'm beginning to think this is a problem with snd-hda-intel, and not with UT's libs. I'm having the same problem with the original Unreal, BTW. Only thing is, I recompiled ALSA a while ago and it didn't help. Perhaps we should file a bug report over at the ALSA page?

---

### Post by Azzco on 2007-02-20
And I just got UT running native... got the same issue as you guys..

---

### Post by diepruis on 2007-02-21
Same sound card?

---

### Post by NTolerance on 2007-04-15
Have any of you tried running UT on Feisty?  Any improvement there?

---

### Post by munckfish on 2007-04-16
Personally not yet as I've only been able to test off the LiveCD so far. I will as soon I've upgraded.

---

### Post by NTolerance on 2007-04-16
Found some interesting stuff here:

[http://www.nevercorner.net/forum/viewtopic.php?pid=9456](http://www.nevercorner.net/forum/viewtopic.php?pid=9456)

I won't be able to test this right now as my new laptop hasn't arrived yet, but it will have the dreaded Intel HDA audio.  If anyone tries those suggestions please post your results.

I also stumbled upon the same fix in the Ubuntu wiki:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuLifebookP7230](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuLifebookP7230)

> In some SDL programs, such as Wesnoth, the audio will contain many scratchy artifacts. This can be fixed by adding the following line to /etc/modprobe.d/options:

options snd_hda_intel position_fix=1 

---

### Post by NTolerance on 2007-04-18
Found a bug report on Launchpad that may be related to this:

[https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483](https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483)

Similar SDL problems reported on the Neverwinter Nights forum:

[http://nwn.bioware.com/forums/viewtopic.html?topic=549178&forum=72&sp=0](http://nwn.bioware.com/forums/viewtopic.html?topic=549178&forum=72&sp=0)

---

### Post by NTolerance on 2007-04-24
I just got my new laptop with the happy funtimes hda_intel sound.  As expected, UT sound is still broken in the exact same way.  I tried all the fixes I posted earlier with no luck.  The real pisser is that I keep finding this very thread at the top of my endless Google searches.

---

### Post by munckfish on 2007-05-08
Now upgraded to Feisty and the problem is still there.

I tried out the 'position_fix=1' thing above. I think it maybe improved the sound a little but still some audible jittering and popping.

---

### Post by mbradlcu on 2007-05-09
here's the fix for the same issue but running quake2:
export SDL_AUDIODRIVER=dsp
I'm not sure if this will work for UT games,, but you may want to modify you're ~/.loki/ut/System/UnrealTournament.ini file changing the following like to the next:
#AudioDevice=ALAudio.ALAudioSubsystem
AudioDevice=Audio.GenericAudioSubsystem

I do this because the AL device positions the sound wrong. hope this helps!

---

### Post by BuddMan on 2007-05-10
Same issue here with the same audio card.  I've even tried git sources kernel and compiled the alsa driver within the kernel.  Anyone got it working yet??

---

### Post by munckfish on 2007-05-11
> **mbradlcu said:**
> 
#AudioDevice=ALAudio.ALAudioSubsystem
AudioDevice=Audio.GenericAudioSubsystem

Thx mbradlcu. Tried it - but it's causing ut to bail out for me. Anyone else any joy with that?

---

### Post by NTolerance on 2007-05-11
I tried both the latest alsa drivers and the Quake 2 sound fix.  Neither worked.

---

### Post by niskel on 2007-12-17
I was having this same problem with the same sound card. I am using ALSA from the Kernel 2.6.24-rc3. Just thought I would mention that using "options snd_hda_intel position_fix=1" as suggested earlier in the thread fixed the problem for me. I don't use Ubuntu so I don't know how relevant this will actually be but thought I would say it works for me.

---

### Post by skoruppa on 2008-01-23
My hda-intel with loki games (like heroes3) have the same problem. To fix just install linux-backports-modules
```
sudo aptitude install linux-backports-modules
```

---

### Post by NTolerance on 2008-01-24
> **skoruppa said:**
> My hda-intel with loki games (like heroes3) have the same problem. To fix just install linux-backports-modules
```
sudo aptitude install linux-backports-modules
```

Now that's interesting.  What exactly does that package do?  Something about updating ALSA to the latest version?

---

### Post by Feanathiel on 2008-04-01
I was reading this forum and I got my UT to work in Linux, however I was facing some sound problems. The sound was all laggy. I managed to fix this by starting the game by entering 'aoss sh ut' in the terminal (not 'aoss ./ut', it will fail). Note: I am using the Generic Audio Subsystem setting mentioned before. Thanks for your support!

---

### Post by Sockerdrickan on 2008-04-05
Use OpenAL Soft to fix it all!

---

### Post by ceasol on 2008-06-02
Is this problem fixed? I have my Dell xps M1330 with the same Intel family sound card and the same problem in Ubuntu 8.04

---

