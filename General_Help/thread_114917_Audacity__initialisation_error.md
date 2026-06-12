---
title: "Audacity : initialisation error"
date: 2006-01-09
forum: General Help
---

### Post by cotcot on 2006-01-09
I installed (synaptic) Audacity because recording with a microphone (the same headset as I use with Skype) and the Gnome default sound recorder only gives a weak sound. Starting Audacity gives an initialisation error of the audio i/o layer.
Has anybody a suggestion ?
Thanks

---

### Post by fangorious on 2006-01-10
System->Preferences->Sound and turn off "Enable sound server startup"

---

### Post by akudewan on 2006-01-10
If that doesn't work, try: ```
sudo killall esd
```

---

### Post by nerval on 2006-01-10
(considering audacity is not installed or removed)
First: 
```
sudo apt-get install libflac++5c2
```
Then:
```
wget http://limpet.net/audacity/ubuntu-breezy/audacity_1.2.4-1_i386.deb
```
And then:
```
sudo dpkg -i audacity_1.2.4-1_i386.deb
```
And finally :)
```
audacity
```

-= For majority of users, this is the end; everything should work properly.  (Don't forget to turn up your mike's volume) =-

Once audacity pops up, go to Edit > Preferences
On Audio I/O tab;  my playback device and recording device says its /dev/dsp.
Don't forget to increase the mike's volume and start recording.

conflict a : if on audio i/o tab; playback device and recording device are empty;
1 - Increase the number of channels, try recording. if it works, 
2 - restart audacity; go back to the Edit > Preferences and you'll now see your playback & recording device folders. 

conflict b : if still not working; 
1- enable "Play other tracks while recording new one" and "Software Playthrough (Play new track while recording it)" while increasing the channel number; 
2 - try recording again. If it works, -=conflict a-2=-

Cheers;
Onur

---

### Post by 146lily on 2006-01-10
**System->Preferences->Sound and turn off "Enable sound server startup"**

works a treat.....thank you very much, it was 'doin my head in'

---

### Post by cotcot on 2006-01-11
Thanks. Disabling the start of the sound server in preferences>sound works fine.
Nevertheless I am going to try the other suggestions too (on my old box) ; it is good for the learning curve.

---

