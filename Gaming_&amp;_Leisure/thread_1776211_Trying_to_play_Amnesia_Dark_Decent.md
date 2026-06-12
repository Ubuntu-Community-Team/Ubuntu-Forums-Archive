---
title: "Trying to play Amnesia: Dark Decent"
date: 2011-06-05
forum: Gaming &amp; Leisure
---

### Post by pepsifx357 on 2011-06-05
I've tried and tried and can't figure it out.  I know what the problem is, but I don't like the solution.

I use a lot of audio editing software so I've got ALSA running.  I've deleted pulse audio and everything to do with it.  Amnesia doesn't like this.  It wants to use pulse audio.  I'm not running a realtime kernel, by the way.

Here is my launcher.log

```
-------- THE HPL ENGINE LOG ------------
Engine build ID 20110509123701

Creating Engine Modules
--------------------------------------------------------
 Creating graphics module
 Creating system module
 Creating resource module
 Creating input module
 Creating sound module
 Creating physics module
 Creating ai module
 Creating gui module
 Creating generate module
 Creating haptic module
 Creating scene module
--------------------------------------------------------

Initializing Resources Module
--------------------------------------------------------
 Creating loader handlers 
 Creating resource managers
 Adding loaders to handlers 
--------------------------------------------------------

Initializing Graphics Module
--------------------------------------------------------
--------------------------------------------------------

Initializing Sound Module
--------------------------------------------------------
 Initializing OpenAL
  Available OpenAL devices:
   0. PulseAudio Software(OpenAL default)
   1. ALSA Software on default
   2. ALSA Software on HDSPM MADI [RME HDSPM MADI] (hw:0,0)
   3. PortAudio Software
  Trying to open device 'PulseAudio Software'... Failed
  Finding first device matching filter that works... 
```

I tried installing pulse and deleting everything ALSA and it actually went into the game but no sound.

Any Ideas?  Something involving ALSA?

Not enough info?

---

### Post by HolgerB on 2011-06-06
Hm, Amnesia works flawless here with a Vanilla 10.04 installation.
I have only out of the box audio configuration though.

---

