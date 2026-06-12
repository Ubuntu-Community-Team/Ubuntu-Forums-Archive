---
title: "buzzing/crackling sound in games"
date: 2009-11-25
forum: Gaming &amp; Leisure
---

### Post by Stosskraft on 2009-11-25
Having funny sounds come from some games such as: tux racer, warzone 2100, and smokingguns.

It is a combination buzz/crackling and in Wolf ET there is no sound at all.

I tried replacing libsdl1.2debian-pulseaudio with libsdl1.2debian-all and no difference.

Any suggestions? My music playback and Videos sound great...only the games are an issue.

Here is the out put of aplay -1:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Shazaam on 2009-11-25
Check the link in my sig and post back if it helped (I have no games on karmic yet lol)...

---

### Post by Vadi on 2009-11-25
[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/485488](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/485488)

---

### Post by Stosskraft on 2009-11-25
Sorry guys, I should add that these games worked fine in 9.04 only since the fresh install of 9.10 do some games not work properly. Even wolf ET worked fine until a restart and then nothing.

---

### Post by Stosskraft on 2009-11-25
> **Shazaam said:**
> Check the link in my sig and post back if it helped (I have no games on karmic yet lol)...

Tried that fix and then I had no sound at all. I then had to go to sound preferences and disable the on board sound and then enable the sound blaster card. The sound returned, but same problem in the games.

Also tried some music in rhythembox and it wasn't as clear as before.

Is there anyway to kind of delete the sound settings and start fresh? Or is this just a bug in 9.10? where it wasn't a problem in 9.04


Thanks

---

### Post by Shazaam on 2009-11-26
Sorry about the no sound result. Edit default.pa and remove tsched=o.

From searching the web there are a multitude of "fixes" that go from removing pulseaudio completely to installing the latest version from source. Of course there are MAJOR risks involved with both ideas such as the removal of the volume control icon and other essential apps/configurations to trashing your sound system to the point that it doesn't work at all. With so many different setups/hardware out there I cannot endorse doing either one. About the only thing I can recommend is to research as much as you can and try different ideas. Or wait for Lucid Lynx and see if the problem goes away :)

---

### Post by Stosskraft on 2009-11-26
Hello Thanks for the info. As I relatively new user I am getting frustrated with the issues in ubuntu. I do think linux is better than windows for me, but I should be able to play a simple games like tux racer with sound, no? 

I understand there is a wealth of info on these forums but I find it too hard to track what to try or how to go about fixing a problem. I write down all changes I make so I can backtrack easily.

I am sure there is some subtle tweaks to get it running, but my 9.10 is too unstable? I mean Wolf Et stopped working quite suddenly yet if I google the sound issues in wolf I get 1000's of different answers. 

I do think the pro's outweigh the con's in regards to ubuntu, but I should be able to play a simple game or watch a movie with some sound right?

sorry to vent

---

### Post by sarareid on 2009-11-26
Hello Stoss,
 I just love this funny sounds coming from the games like tux racer, warzone 2100, and smokingguns.I know that well that it is a combination buzz/crackling and in Wolf ET there is no sound at all.There will be no difference replacing libsdl1.2debian-pulseaudio with libsdl1.2debian-all.There is no way that you can stop this sonds unless you turn off your speakers.Thank you.

---

### Post by Stosskraft on 2009-11-26
sarareid;

Sorry I do not understand your post. If your trying to mock me that's great, but your sarcastic tone is not appreciated.

I find it hard to believe that this problem does not have a solution, I just need some guidance as it seems that sound problems is fairly common in ubuntu.

The reason I post is because I find the amount of information can be over whelming  and I would like input on my specific case as it seems everyone's PC set up is a little different. 

Thank you

---

### Post by brian70809 on 2009-11-29
There is a thread on this on the forums.. but I'm going to tell you what I just did based on it.

go to your System->Preferences->Sound settings

Go to the Hardware Tab.. and click the profile arrows..  Change it to another setting...  try game out... then put it back to the default..   which for me was "Analog Stereo Duplex"...

and VOILA.. no more crackling..

---

