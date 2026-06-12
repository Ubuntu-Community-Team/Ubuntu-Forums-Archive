---
title: "Does bluetooth headset require pulseaudio"
date: 2009-04-19
forum: General Help
---

### Post by strider22 on 2009-04-19
When I use system/preferences/sound and test the three choices; Alsa, OSS and pulseaudio only the Alsa option works (and of course autodetect).

The instructions I find for using a bluetooth headset are based on pulseaudio. Is pulseaudio required or can I make this work with Alsa? 

If you think you are using Alsa, when you open the system/preferences/sound app and test the options does pulseaudio fail for you?

Here is the message I get when I test pulseaudio;
```

audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink: 
Failed to connect: Connection refused
```

It has taken 12 hours of web search and trial to find out how to pair the device. I have now updated that info in several places on the web and I have now decided to write a proper installation guide so your help would be appreciated.

---

### Post by strider22 on 2009-04-20
Bump

---

### Post by sdennie on 2009-04-20
As far as I know, nothing requires PulseAudio.  In fact, the default sink for PulseAudio is ALSA.  So, it's a level indirection that you can easily uninstall and do without.

---

### Post by strider22 on 2009-04-20
Thanks for the reply.
Do you have bluetooth?
Can you verify that you don't have pulseaudio via the steps given above.

The Bluetooth Headset instructions at;
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

include this step;
```

Now we need to tell PulseAudio that your Bluetooth headset exists 
by running the following commands in a terminal:
    *
      pactl load-module module-alsa-sink device=bluetooth
      pactl load-module module-alsa-source device=bluetooth

```

---

### Post by strider22 on 2009-04-21
Upon further investigation and thought, I have decided that if you are adding a bluetooth headset then you will have two choices of where the music should come out; the headset or the speakers.

Since pulseaudio is a switch box that allows easy control of where your music goes out, as well as where it comes in, that it should be installed. Yes there also are other mixers but from all the reading I've done pulseaudio seems the most popular.

I'm going to install pulseaudio and do for the instructions I will make pulseaudio a requirement.

---

### Post by sdennie on 2009-04-21
> **strider22 said:**
> Upon further investigation and thought, I have decided that if you are adding a bluetooth headset then you will have two choices of where the music should come out; the headset or the speakers.

Since pulseaudio is a switch box that allows easy control of where your music goes out, as well as where it comes in, that it should be installed. Yes there also are other mixers but from all the reading I've done pulseaudio seems the most popular.

I'm going to install pulseaudio and do for the instructions I will make pulseaudio a requirement.

I understand your sentiment but, it's not strictly true.  I don't run PulseAudio on my machine and via the standard ALSA mixers can redirect my sound output from the speakers on my laptop to an HDMI cable to a TV.  Very, very easily.  PulseAudio is not strictly needed unless you need your sink (output) to be be something other than what ALSA handles (let network connections).

---

