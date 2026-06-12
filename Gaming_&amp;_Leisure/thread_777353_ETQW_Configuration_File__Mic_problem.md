---
title: "ETQW: Configuration File / Mic problem"
date: 2008-05-01
forum: Gaming &amp; Leisure
---

### Post by tim_wright on 2008-05-01
Hello all, thanks for reading in advance!

This issue relates to microphone use in ETWQ. Below is some system information:

OS:         Ubuntu 8.04 LTS (Hardy Heron)
Sound:      PluseAudio (ALSA plugin used with ETQW)
Game:       Enemy Territory Quake Wars v1.4 Native Linux Client
Microphone: Yes, and working. Plugged in at the back of my PC. 

Here is the relevant extract from my *etqwconfig.cfg* file:

```
seta s_micDevice ""
seta s_voiceDevice ""
seta s_primaryDevice ""
seta s_driver "alsa"
seta s_device "/dev/dsp"
seta s_noMic "0"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_mic ""
seta s_alsa_pcm "default"
seta s_maxLowPrioritySounds "8"
seta s_useAdpcmCompression "1"
seta s_numberOfSpeakers "2"
seta s_globalFraction "0.8"
seta s_subFraction "0.75"
seta s_playDefaultSound "1"
seta s_volume_VoIPScale "1"
seta s_volume_VoIPOut_dB "-2.449976"
seta s_volume_VoIPIn_dB "-3"
seta s_volume_dB "0"
```

My microphone records perfectly WITHOUT ANY MIC BOOST via *Sound Recorder* in the menu *Sound & Video*. The sound is played back perfectly as well. The microphone input volume volume is at full. 

The problem occurs when I try and send audio via ETQW. I cannot seem to get the setting correct. Also, when I managed to get it correct, only some people could hear my transmitted audio. 

As a summary I would appreciate it if someone / multiple people who have properly working configurations could share the file located in:

/home/YOUR-USERNAME/.etqwcl/base/etqwconfig.cfg

Thank you once again,
Tim

---

### Post by DSK on 2008-05-02
Hey Tim,

I dont have the game you are talking about but I do have a suggestion.

In terminal

[HTML]alsamixer[/HTML]

Then hit "F4" to list only capture devices.

Try adjusting the volume's up on some of those settings.  Perhaps when using pulse audio it use's different input settings then in Sound Recoder.

I know for me my mic is controlled with "MIC" and "Analog M" settings for just alsa (what I hear in Sound Recoder and in TeamSpeak".  

Best luck

DSK

---

### Post by tim_wright on 2008-05-03
Thanks very much. I was changing too many variables at once. Here are some screenshot of my config so that other people may benefit if they have the same problem:

[ATTACH]68585[/ATTACH]

I kept the digital channel down low as amplifying a digital channel gives a lot of noise (trial and error)

[ATTACH]68586[/ATTACH]

Muted any unused channels (forgot to mute mic boost). I also left the config file to its default settings ;)

Thank you for your help :)

---

