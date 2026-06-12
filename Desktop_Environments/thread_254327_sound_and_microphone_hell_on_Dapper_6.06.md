---
title: "sound and microphone hell on Dapper 6.06"
date: 2006-09-09
forum: Desktop Environments
---

### Post by kpm on 2006-09-09
I have an old IBM Thinkpad (A22M). Upon install of Dapper, it seemed everything was working (aside from having to enable the sound and microphone... which cost me about an hour while I searched for solutions rather than clicking on the speaker icon to enable right away... sigh).  But once speakers and microphone were enabled I could speak into the microphone and hear my voice comming out of the laptop speakers.  Progress!!  Then, I ran Skype, all hell broke loose, after much reading, I went and grabbed the beta version, then it seemed to work, it dialed out, I could hear the person I was calling, and I could hear myself in the speakers when I spoke in my microphone.  Unfortuantely, the party on the other line could not hear me... I tried other voip apps as well, thinking it was a Skype only problem, but it turns out that my microphone does not transmit sound to the receiving computer, even though I can hear myself through the laptop speakers when I talk into the microphone.

Soooo back to the forums, google, linux how to's, etc.  I ensure ALSA is selected for the audio device... The Dapper I installed did not create a asound.conf file, I read about that, then followed a few different instructions for creating it, changing esounc.conf, etc.  I have done much trouble shooting over the last few days and have gotten no where (accept a bit closer to bowing, tired and beaten, to the alter of Bill Gates)

The soundcard, according to the Device Manager is a 'CrystalClear SoundFusion Audio Accelerator'.  Other settings in the Device Manager regarding sound are:
CS46xx ALSA Capture Device
CS46xx ALSA Control Device
CS46xx ALSA Playback Device
CS46xx Rear ALSA Playback Device
CS46xx IEC958 ALSA Playback Device
CS46xx OSS MIDI Device
CS46xx OSS MIDI Device
CS46xx OSS Control Device
CS46xx OSS PCM Device
CS46xx OSS PCM Device
CS46xx OSS PCM Device

as well, here is a list of hardware playback devices grabbed with 'aplay ls':
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
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
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
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
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]

Can anyone help??

Thanks

---

