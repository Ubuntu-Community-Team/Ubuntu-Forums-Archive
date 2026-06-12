---
title: "PLEASE how do you tell alsa which device to use!?!??"
date: 2009-04-24
forum: General Help
---

### Post by daverich on 2009-04-24
This seems so silly.

I installed ubuntu Ibex which I've just upgraded to Jaunty and now I've no sound.

I suspect the problem is because when I installed Ibex i had my webcam and headset plugged in and alsa started to use the camera as the main device - stupid but there you go.

HOW on earth do you tell alsa which device to use. Why isn't there a simple checkbox? - or is there?

Please help this is driving me mad.

Also pulseaudio does nothing at all, no sound whatsoever.

Before in ibex I could at least get sound using the OSS option in SOUND.

Kind regards

Dave Rich

---

### Post by daverich on 2009-04-24
reformatted and reinstalled from the live cd and now all is well.

I'd still like to know why there isn't a simple device chooser though.

Kind regards

Dave Rich

---

### Post by kostkon on 2009-04-24
> **daverich said:**
> reformatted and reinstalled from the live cd and now all is well.

I'd still like to know why there isn't a simple device chooser though.

Kind regards

Dave Rich
There is, it's called *PulseAudio Device Chooser*. You can install it from *Synaptic*.

Hope that helps.

---

### Post by daverich on 2009-04-24
> **kostkon said:**
> There is, it's called *PulseAudio Device Chooser*. You can install it from *Synaptic*.

Hope that helps.

yeah, which doesn't tell all the apps who use alsa, not pulseaudio,- what device to use.

Kind regards

dave rich

---

### Post by paradigm2 on 2009-04-24
```

lspci

```

Which sound card do you have?  If it doesn't eve see it, stop here.  What is below won't help until this is fixed.

Make sure these are correct:

1. Try System -> Preferences -> Sound
2. Try Applications -> Sound and Video -> Pulse Audio Device Chooser
(You may not have this, if not: install pavucontrol)
3. Also check Applications -> Sound and Video -> AlsamixerGui
(If you don't have it, install alsamixergui)  Incidently also make sure the settings here are turned up so that you may hear the sound.

---

