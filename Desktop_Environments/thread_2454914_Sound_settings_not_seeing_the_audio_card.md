---
title: "Sound settings not seeing the audio card"
date: 2020-12-08
forum: Desktop Environments
---

### Post by kakotako on 2020-12-08
Ubuntu 20.10, Gnome 3.38.1.

All of the sudden the Gnome sound settings is not seeing any output devices in the Settings/Sound dropdown menu. The sound playback is actually working. Alsa Mixer can control the volume, but my dedicated volume up/down keys, mute mic/speakers keys, and their corresponding LEDs are not working. The volume slider in Settings/Sound has no effect.

I reinstalled pulseaudio, let it reubuild ~/.config/pulse. That didn't help. Then I created a new user. The new user has the sound control. Therefore the problem is not system-wide. I'm guessing it may be Gnome related. The only Gnome relevant thing I did before I lost the sound control was to disable the built-in Desktop Icons in Extensions and add Desktop Icons ng (ding) extension in Tweaks. 

I appreciate any tips to regain the sound control.

[IMG]https://ibb.co/kDfdtwZ[/IMG]

---

### Post by ActionParsnip on 2020-12-09
Please use this guide
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Give the output of step 3

Thanks

---

### Post by kakotako on 2020-12-09
The issue had to do with Pulseaudio. The daemon was not able to start due to changed permissions somewhere in the affected user's home directory. The Pulseaudio log gave:
[FONT=Courier New]E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied[/FONT]

Which was easy to solve with:
[FONT=Courier New]sudo chown -R $USER:$USER $HOME/[/FONT]

---

