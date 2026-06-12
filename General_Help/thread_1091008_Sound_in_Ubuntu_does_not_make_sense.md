---
title: "Sound in Ubuntu does not make sense"
date: 2009-03-08
forum: General Help
---

### Post by f.sardis on 2009-03-08
Can someone briefly explain to my why we have ALSA, OSS and PulseAudio all installed together? I cannot understand why we need ALSA if Pulse or OSS is there.
When I open up the volume control i the following devices and each one has its own controls, some of which do nothing while some others are linked between devices:

HDA Intel (ALSA Mixer)
Realtek ALC268 (OSS Mixer)
PLayback: ALSA PCM on front: 0 (ALC268 Analog) via DMA (PulseAudio Mixer)
Capture: Monitor Source of ALSA PCM on front: 0 (ALC270 Analog) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on front: 0 (ALC270 Analog) via DMA (PulseAudio Mixer)


I cannot understand what this list represents. I got one mic embedded in the laptop's screen, one input jack, one mic jack and one output jack and of course the laptop speakers. Can someone explain to me what is this mess?

---

### Post by miegiel on 2009-03-09
"System > Preferences > Volume control"
Is to regulate and turn on/off in- and outputs.
under "Edit > Preferences" you can select channels hidden by default

"System > Preferences > Sound"
Let's you select which sound device to use for different tasks. You can chose software devices like OSS, ALSA and Pulse, or pick a hardware device and there is autodetect too.

Some links If you want to know more about OSS, ALSA and Pulse
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)
[http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture](http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture)

I'm in a wikipedia mood today I guess :twisted:

---

### Post by f.sardis on 2009-03-09
yes, wiki is the first stop but it does not mean it is an accurate source of info. If we go by what wiki says then we should have only one server running. Alsa is a replacement for OSS and pulse is replacement to alsa according to them. 
They fail to explain why i am running all 3 of them on my laptop too. 
I did not ask for configuration settings, just some info on what is going on with the sound servers. Even hardware devices have a sound server attached to them which makes no sense either. As a matter of fact my device is listed 3 times. Twice with OSS and once with ALSA in the sound preferences.

---

### Post by miegiel on 2009-03-09
The volume control is just levers to adjust stuff, What you want to adjust depends on what you're using or you application is using. However, you can't select which device you want to use in volume control. You can do that in "System > Preferences > Sound" or often in the applications themselves to override the ubuntu setting.

---

### Post by emarkay on 2009-03-09
What Ubuntu version - I get what's attached when I hit "preferences":

---

### Post by f.sardis on 2009-03-09
My question is why do we need alsa and oss and pulse all running at once when only one of them is necessary to deliver audio?
I am running intrepid. Sound works fine apart from recording through the line in or mic jack. those two just give me noise, pops and cracks and very feint sound in the background. i would love to get those working properly but they are not a high priority at the moment. I suspect the problem i am having is due to all the sound servers working at once and each one boosting the signal to the point it distorts. the embedded mic seems to work fine though.

---

