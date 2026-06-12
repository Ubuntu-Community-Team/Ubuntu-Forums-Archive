---
title: "Xubuntu volume control issue"
date: 2009-01-02
forum: General Help
---

### Post by Chew N Tobacca on 2009-01-02
I have been fiddling with Xubuntu 8.10 for since its release, after using Ubuntu since 7.10. I have ran into an issue with volume/sound devices. Perhaps there is something obvious I am missing...
Searched through forums and web, still no solution.
I have installed PulseAudio, which seems to be doing its job. However, the "master" volume control is ineffective; "master" is apparently always at 100% regardless of what it is set to. Seems to be controlled by each individual app.
On my system, I have the onboard sound (Intel 82801) and a TurtleBeach Audio Advantage Micro USB sound device. Here is my output from running "aplay -l":
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio       ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I can switch devices by opening sounds dialog (apps -> prefs -> sound) and the running "asoundconf set-default-card" then a reboot. But the same issue is still at hand: Volume is blasting!

Under GNOME desktop, I can simply open the Sound options dialogue and set the playback device to the desired output, works great on the spot. But with xfce, I am stumped...
Any input is appreciated.

---

