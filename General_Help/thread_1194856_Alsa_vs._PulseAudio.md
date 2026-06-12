---
title: "Alsa vs. PulseAudio"
date: 2009-06-23
forum: General Help
---

### Post by Mikael P. on 2009-06-23
Hey again forum,
I am wondering how to get this sorted? When I installed Ubuntu a few days ago I wanted my sound to work. So I happily googled and found something about Alsa which I followed. Suddenly I could hear!
But now having become a bit more familiar with things I realised I had something else, PulseAudio which might be competing with Alsa.

In the volume control I can choose my soundcard which has entries where it's either controlled by Alsa or PulseAudio. Lowering the volume on either one affects the audio.

But as I couldn't hear anything when I played mp3's before installing Alsa I don't really know what to do.

So, could anyone point me in the direction I should go?

---

### Post by CatKiller on 2009-06-23
> **Mikael P. said:**
> So, could anyone point me in the direction I should go?

Don't worry about it. Whatever it was that you installed, it probably wasn't ALSA since that its already installed by default. It may have been some optional component.

ALSA and PulseAudio do different things. It's ALSA that actually spits the sound to the soundcard. PulseAudio manages the sound before it needs to be output; mixing different audio streams, applying effects, sending them over the network, that kind of thing. Once it's done with the stream, it passes it on to ALSA to actually play the sound with the soundcard. You're supposed to have them both.

It's possible to bypass PulseAudio and just use ALSA directly, which is what some people choose to do because of configuration problems. But you don't have to.

Being able to control the volume - whether the soundcard is controlled by either PulseAudio or ALSA - is desirable, don't you think? If using one or the other meant that you could no longer control the volume, it would mean that whichever one didn't work was broken.

---

### Post by kerry_s on 2009-06-23
yeah, pulseaudio is just a layer on top of alsa, just think of it as a mixer. alsa does the real work and pulseaudio deals with the programs, think middle management. :D

---

### Post by TheExplorer on 2009-06-23
It's not a layer, not a mixer and not a middle management either. It is a sound server. Speak Linux, people ;)
In fact it's a networked sound server project intended to be an improved drop-in replacement for the Enlightened Sound Daemon (ESD). Read [here]("http://en.wikipedia.org/wiki/PulseAudio"). Well, wiki is not a good thing, just for you to get the meaning.

---

### Post by Mikael P. on 2009-06-23
Cheers for clearing that up! I thought it might be related to why certain other aspects of the sound does not work properly in my system.

Could you enlighten me as towards where I can find more info about the sound devices on my system? As I have both a proper soundcard and one on my mainboard.
I thought that maybe by disabling the ones I don't use I could get the keyboard volume control actually control the card I am using.

Another thing regarding audio. Why is it that sound works in certain applications and not in others? Do I control their output individually?
I am thinking of the default video and audio tools that came by default with Ubuntu.

---

### Post by kostkon on 2009-06-23
> **Mikael P. said:**
> Cheers for clearing that up! I thought it might be related to why certain other aspects of the sound does not work properly in my system.

Could you enlighten me as towards where I can find more info about the sound devices on my system? As I have both a proper soundcard and one on my mainboard.
I thought that maybe by disabling the ones I don't use I could get the keyboard volume control actually control the card I am using.

Another thing regarding audio. Why is it that sound works in certain applications and not in others? Do I control their output individually?
I am thinking of the default video and audio tools that came by default with Ubuntu.
You need to install the *PulseAudio Device Chooser* utility (using *Synaptic*). It will allow you to set a default audio device in your system, control the volume levels of every application individually and on-the-fly and some other things.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384"), if you want.

---

### Post by kerry_s on 2009-06-23
> It's not a layer, not a mixer and not a middle management either. It is a sound server. Speak Linux, people 

over simplified to much? :D

> Thus, applications using ALSA will output sound to PulseAudio, which then uses ALSA itself to access the real sound card. 

pulsesaudio-->alsa

your right, no middle management/layer there. :D

---

### Post by hibliss on 2009-06-23
I use Pulseaudio Volume Control (pavucontrol) and it allows me to pick what sound device each audio stream goes to. I can have my PC playing music over bluetooth and firefox routing sound to external speakers at the same time. Pulseaudio is awesome.

---

### Post by kerry_s on 2009-06-23
actually you don't even need pulseaudio at all, you can just uninstall it & use alsa directly. i don't use pulseaudio.

---

### Post by Mikael P. on 2009-06-23
hmm. It sounds quite useful, even though I don't have a setup that advanced so I would use it.
Apparently I already had the pulse audio device and volume control installed. Although it was only the volume control that worked. For some reason the device chooser does not start, it only gives me the wait pointer.
I can set my default device in the volume control though, but there is another volume control at the top panel which seems to be controlled by something else. I couldn't find any name attached to it. That default one ignores my settings I do in the pavucontrol window.
How do I make it behave?

I am really grateful for all your opinions and pointers, I am learning a lot!

---

### Post by CatKiller on 2009-06-23
> **Mikael P. said:**
> there is another volume control at the top panel which seems to be controlled by something else.

Right-click on it and select Preferences. You can select which device this volume control controls.

---

### Post by Mikael P. on 2009-06-24
Yes, I tried that. But maybe I wanted to do too much? I was hoping that changing the default device would make my keyboard control the default device, not the one it fancied.
Maybe I better go google logitech media keyboard then.

---

### Post by CatKiller on 2009-06-24
> **Mikael P. said:**
> I was hoping that changing the default device would make my keyboard control the default device, not the one it fancied.

You should have said.

System -> Preferences -> Sound. Default mixer tracks at the bottom. Pick a device, then select the channel that you want the keyboard to control. Master is probably a good bet.

> Select the device and tracks to control with the keyboard. Use the Shift and Control keys to select multiple tracks if required.

---

### Post by Mikael P. on 2009-06-24
I found a tool called KeyTouch which let me define which volume control my keyboard actually got linked to. When I changed it to pavucontrol everything works fine.
I tried your way too but couldn't get it working. Probably because I am new to all this...

---

