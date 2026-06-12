---
title: "sound broken in kde after upgrade"
date: 2005-04-27
forum: Desktop Environments
---

### Post by verzonen on 2005-04-27
After upgrade of kdelibs? (uninstall knetworkconfig? and installing it again) my sound is no longer working

When I start up the system and go to a console (ctrl+shift+F1) sound works fine.  However if i go back to kde (ctrl+shift+F7) and proceed to log in, I get this error message;

Sound server informational message:
Error while initializing the sound driver:
device: /dev/dsp1 can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.

if I type in cat /usr/lib/openoffice/share/gallery/sounds/train.wav > /dev/dsp1 as suggested in another forum, I do get sound, I tried fidling with the soundsytem settings in "soundsystem controll center" but no luck sofar.

---

### Post by verzonen on 2005-04-27
After selecting oss (Open SOund System) and override hardware device in "sound system controll center"/hardware sound is working again... 

huray......

---

