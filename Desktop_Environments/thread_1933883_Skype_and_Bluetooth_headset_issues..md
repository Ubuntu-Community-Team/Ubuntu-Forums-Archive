---
title: "Skype and Bluetooth headset issues."
date: 2012-03-01
forum: Desktop Environments
---

### Post by alekons on 2012-03-01
Hi,

I have issues connecting my Bluetooth headset to skype. Although that i pair my headset the SKype doesn't give me an option from the settings to select it.

I have Ubuntu 10.10 64bit, Skype for linux 2.2.0.35 and Pulse Audio.

[IMG]http://img263.imageshack.us/img263/9311/20120301101220.png[/IMG]

---

### Post by kostkon on 2012-03-01
Either set your headset as the default input and output device for your system in your sound preferences (don't worry, PulseAudio will fallback to the next available device every time you disconnect your headset) or install the *PulseAudio Volume Control* utility (use the software centre to install it).

Run this utility, start a call in Skype and then you should see this application listed in the Playback and Recording tabs; just select your headset from the list of available devices. This way you will set your headset as the input and output device *only* for Skype and thus you will avoid the need to set it as the default device system-wide.

Hope that helps.

---

