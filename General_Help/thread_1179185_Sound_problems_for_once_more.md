---
title: "Sound problems for once more"
date: 2009-06-05
forum: General Help
---

### Post by Lockheed on 2009-06-05
I confugired pulseaudio according to the most recent guides. I installed newest release of Alsa. I though that finally everything is working well.

Well, as usual with ubuntu, it wasn't.

Plying flash = no sound in mplayer and VirtualBox but vlc is not affected.
Playing mplayer = No sound in flash and VB (vlc still works).

What else can I do?

---

### Post by Soul-Sing on 2009-06-05
You did install the Mplayer Plugin for Firefox?
did you try to start mplayer via the terminal? ```
gmplayer
```
Did you install some restricted formats? (w32codecs/libdvdcss2)
Did you try to disable pulseaudio and enable alsa? (and how?)

---

### Post by Lockheed on 2009-06-06
> **leoquant said:**
> You did install the Mplayer Plugin for Firefox?
did you try to start mplayer via the terminal?
No. The only way I'm using mplayer is through screenlets' plugin "radio",

> Did you install some restricted formats? (w32codecs/libdvdcss2)
I don't know. After installing ubuntu, I followed a guide for enabling it to play all the popular formats. But anyway, I supposed it has nothing to do with the problem, as this occured just recently.

> Did you try to disable pulseaudio and enable alsa? (and how?)
How do you mean?

---

### Post by Soul-Sing on 2009-06-06
system: preferences: sound. Did you some "soundtesting"?
tried 'alsa'?

Are you listening streaming radio/audio via mplayer? then rythmbox is very useful. You can easily add some streaming strings en manage streaming radio/audio.

---

### Post by Lockheed on 2009-06-06
> **leoquant said:**
> system: preferences: sound. Did you some "soundtesting"?
tried 'alsa'?
Everything is set to PulseAudio. If I set it to ALSA and click TEST I get this:
```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. Device is being used by another application.
```


> Are you listening streaming radio/audio via mplayer? then rythmbox is very useful. You can easily add some streaming strings en manage streaming radio/audio.
The only reason I am "using" mplayer is because it is being used by the screenlet called RADIO. I never actually see mplayer, I just click "play" on screenlet's panel and then in System Monitor I can see mplayer process.
I doubt this screenlet can be configured to use anything else.

---

### Post by Lockheed on 2009-06-07
Well, I installed Pulseaudio 0.9.15 but it changed nothing.

---

