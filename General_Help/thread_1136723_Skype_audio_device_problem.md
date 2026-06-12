---
title: "Skype audio device problem"
date: 2009-04-25
forum: General Help
---

### Post by tubunu on 2009-04-25
For the life of me, I cannot get Skype to work at all... I'm on a fresh Jaunty install, you'd think this should work out of the box. It doesn't. :(

I checked System/Preferences/Sound - everything works. In Sound capture tab, the sound from my microphone gets *a lot of latency* but it does work with ALSA setting. 

"Make a test sound" in Skype Sound devices doesn't produce ANY sound at all. 
Trying to make a Skype test call, it gives me "Problem with audio capture".

Could someone who got it working please share a how to? Thanks. 

My soundcard is Audigy2 ZS. Skype works perfectly when I boot to Window$.

> ~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [2001]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [2001]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [2001]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [2001]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by JoaoMachado on 2009-04-25
I had the same problem, I had to go into Options>Sound and change the "Sound In" and "Sound Out", from Default to your actual Sound Card driver.

I have an Intel Sound Card on my HP G60 Laptop, so I changed both settings to HDA Intel (hw:Intel,0)

It now works, but it is not as stable as in Intrepid.

Joao

---

### Post by ACMiller on 2009-04-25
Hey, I had the same problem on a fresh intall of Jaunty. I think the problem may be in how skype detects your default audio device. Just like JoaoMachado I went to options in skype and to the sound tab, and changed all my devices to pulse-audio. Then everything worked fine (and just as stable as before). My mic volume was low though so I had to enable turn up the mic booster volume under volume control. If you can't see a slider for mic boost you can add it by selecting it under preferences in that window. Good luck

---

### Post by joker77 on 2009-04-26
[http://linuxtipstricks.wordpress.com/2009/04/04/how-to-permanently-fix-skype-audio-problem-in-ubuntu/](http://linuxtipstricks.wordpress.com/2009/04/04/how-to-permanently-fix-skype-audio-problem-in-ubuntu/)

Anybody tried the suggestions in the above site?

I have the same problem, and the suggestions given in the earlier posts in this thread are not working for me on jaunty.  Want to check if those lines in that link are ok for me...

---

### Post by nortexoid on 2009-04-26
I had the same problem as well and the following worked. According to the community documentation, you should set your Sound In and Sound Out to "pulse" if it's available.

However, I still have the problem of audio capture flaking out every few minutes. I have to keep switching it around to get it to work, during a conversation. I'm hoping Ekiga works better--it's just a pain getting others who use Skype to use Ekiga. Anybody have any experience comparing the two?

---

### Post by joker77 on 2009-04-27
[http://www.johannes-eva.net/index.php?page=skype_jaunty](http://www.johannes-eva.net/index.php?page=skype_jaunty)

The suggestions given in the above link worked for me! Moreover they are changes that can be easily reversed.

For better performance I slightly increased the "capture" under Recording in "Volume Control" & then unchecked "allow skype to automatically adjust mixer settings" but that is not really necessary.

Please note: for me, in volume control, under Options, it had been Mic. That could well have been the only (or main) culprit??

Previously audio recorder was not playing back (probably not detecting any sound). now that's working well. You can use that along with the volume control -> recording -> capure slider to fine tune the loudness of your voice.

I'm on a HP Pavilion dv6000 series laptop, jaunty, using the laptop speaker and front mic (above the screen). 

My mixer settings are as in the attachments (essentially same as on johannes-eva.net). 

Hope this works for others also:)

Now to find someone to call....

PS: to get all those options in the Volume control, go to preferences and select everything. (the kind of thing I would spend hours searching for)

---

### Post by johnaaronrose on 2009-04-28
I've tried johannes eva's instructions referred to above.  Only difference is that the Options (in Gnome Volume Control) only gave 'mic' option for 'input source'.  Speaker works (either using speakers or on cheapo phone device or on headset) but not sound capturing (i.e. me speaking) on cheapo phone device or headset. I've also tried a USB webcam which shows picture but does not capture sound either. I've tested this on both skype making a test call and making a real call using skype. I then tried Sound Recorder from the Sound & Video menu. That does not record. I've tried this all on both a laptop & a desktop. Looks like problem with Ubuntu Jaunty. Any ideas?

---

### Post by johnaaronrose on 2009-04-29
Problem in jaunty is that not all pulse audio packages are installed and sound needs to be configured for pulse audio. This has at least one other advantage: can directly record sound from computer input e.g. playing radio station. URL for solution is:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

