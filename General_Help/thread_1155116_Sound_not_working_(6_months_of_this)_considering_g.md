---
title: "Sound not working (6 months of this) considering going back to windows"
date: 2009-05-10
forum: General Help
---

### Post by d3drocks on 2009-05-10
hello.
Im ******* PISSED at this right now. audio worked on 9.04 jsut fine. I upgraded and its gone to ****. I went into the audio preferences, and the OSS driver tests with sound when I hit the test button. BUT ONLY AUDIO PLAYBACK APPS FOR OGG AND MP3 FILES WORK, AND PIDGIN MAKES ITS BEEPING SOUND. NO OTHER SOUND IS GENERATED.
I typed in lspci into the terminal, and it outputted this as my audio device:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
```
I have an HP Pavilion.
someone told me to use killall to end pulse audio, then try using ALSA, but alsa jsut gives me an error:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```
If I cant find a fix for this, im just going back to windows. I need sound for what I do.

edit:
some more output from the terminal:
```
     *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

---

### Post by danwood76 on 2009-05-10
Pulsedaudio auto starts itself, so just killing it wont get rid of it as it will just start up again.
You should be able to get pulse working nicely but it can take a bit of messing around.

First I would make sure that everything in the sound preferences is set to auto, if you have these set to anything else then it could interfere with pulse. When they are set to auto do a test if you hear sound then good.
If you dont try playing with alsa volume controls for the pulseaudio device.

Also another good tip when writing a thread is to not start it with an insult or a threat of switching OS (like we really care if you switch to windows)

---

### Post by russo.mic on 2009-05-10
I can honestly say that I don't really care.

---

### Post by bootyhunter on 2009-05-10
I had the same problem for a few days. Tests would work but nothing else would produce sound. I thought it was my sound drivers at first, but that wasnt the problem. It sounds stupid but I just went into my volume control and pushed up the Master Volume bars to max. They were already 75% up, but when I put it all the way up, everything worked. I dont know if this will work for you, but its worth a shot if you haven't tried it.

---

### Post by d3drocks on 2009-05-10
> **danwood76 said:**
> Pulsedaudio auto starts itself, so just killing it wont get rid of it as it will just start up again.
You should be able to get pulse working nicely but it can take a bit of messing around.

First I would make sure that everything in the sound preferences is set to auto, if you have these set to anything else then it could interfere with pulse. When they are set to auto do a test if you hear sound then good.
If you dont try playing with alsa volume controls for the pulseaudio device.

Also another good tip when writing a thread is to not start it with an insult or a threat of switching OS (like we really care if you switch to windows)

its not an insult. its a sign of mass frustration. I spent time in the IRC channel asking for help, no one was able to do anything. Ive made threads about it here in the past, and no one was able to help at all. I am extremely pissed, so sorry if it came accross as an insult. I didnt mean it as that.

If I set everything to auto, it detects all the wrong stuff, and I get no sound at all (instead of just a few things working. i get that same error I put in the code thingy in my first post.)
I already tried messing with the alsa volume controls, with no success as well.

> I can honestly say that I don't really care. 
I can honestly say that you are a moron.
if you dont like what I have to say, then dont talk to me...idiot.


> **bootyhunter said:**
> I had the same problem for a few days. Tests would work but nothing else would produce sound. I thought it was my sound drivers at first, but that wasnt the problem. It sounds stupid but I just went into my volume control and pushed up the Master Volume bars to max. They were already 75% up, but when I put it all the way up, everything worked. I dont know if this will work for you, but its worth a shot if you haven't tried it.
Also tried this. doing that is what managed to get pidgin to beep. still the same outcome from everything else though.

---

