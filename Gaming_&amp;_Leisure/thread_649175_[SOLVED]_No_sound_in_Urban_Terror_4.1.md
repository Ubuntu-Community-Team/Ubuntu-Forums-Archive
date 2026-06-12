---
title: "[SOLVED] No sound in Urban Terror 4.1"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by TidusBlade on 2007-12-24
Just downloaded and installed it today, the ioUrbanTerror, even though I have Quake 3, but I didnt know. Anyways, theres totally no sound anywhere in the game, and all other programs aren't outputting any sound. I have only OSS though and ALSA is disabled so maybe thats it? 
Any help is welcomed, Thanks!

---

### Post by MasterRex on 2007-12-26
Are you attempting to run UrT 4.1 through wine? o.O

There is a .zip with everything supposedly needed to install/run; but I can't get anything to run... I've even tried forcing some of the files to be executable with chmod +x. 

Has anyone been able to play UrT 4.1 successfully on *any* distro?

---

### Post by TidusBlade on 2007-12-26
Never mind, got it fixed. Why WINE it when theres native linux binaries? 
Anyways, I had no ALSA, only OSS so sound didnt work, fixed now, just forgot to mark the thread as Solved...
*marks it solved*

---

### Post by defaulk on 2008-05-07
How did you fix?  Did you get UT to use ALSA?

---

### Post by svbh07 on 2008-05-08
> **MasterRex said:**
> Are you attempting to run UrT 4.1 through wine? o.O

There is a .zip with everything supposedly needed to install/run; but I can't get anything to run... I've even tried forcing some of the files to be executable with chmod +x. 

Has anyone been able to play UrT 4.1 successfully on *any* distro?

I believe this will be different depending on your CPU, but I just execute ioUrbanTerror.i386. I'm running Hardy.

---

### Post by baytuni on 2009-10-07
I hate when people do that. Open a thread and somehow solve it and say " nevermind I solved it thanks". You should write how you'd solved it. That's how all this community works.

---

### Post by baytuni on 2009-10-20
ok I have no sound in UT now the problem is UT does not know which driver to use, at least I am guessing so,

```
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
--------------------------------

```

anyone has any idea?

---

### Post by life4himsq on 2009-11-17
baytuni, are you using ubuntu 9.10 without any modifications? I am not sure about your problem but I might be able to help. I had a sound issue pop up about 2 or 3 weeks ago where the sound might be there for the first second of the intro but never come back. It shows up under pulseaudio management but never comes out of the computer til I reboot. Then it works for a few games and then one time I open UrT and no sound again. Here is what mine shows:

[HTML]------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x226a000 dma buffer
No background file.
----------------------
Sound initialization successful.[/HTML]


You could try typing 
[HTML]gstreamer-properties[/HTML]

in the terminal. This gives you a gui to setup what sound server is used by default.

---

### Post by baytuni on 2009-11-18
Thanks for the reply. I already solved my problem but I guess I forgot to mention here. I solved it by installing libsdl-1.2debian-alsa package.

---

### Post by Rob-e on 2010-03-13
installing libsdl1.2debian-pulseaudio fixed it for me

sudo apt-get install libsdl1.2debian-pulseaudio

---

### Post by Tikkyca on 2010-03-13
Sound works perfect on every my game,except assault cube,smoking guns,and open arena.

---

