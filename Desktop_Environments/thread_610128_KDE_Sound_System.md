---
title: "KDE Sound System"
date: 2007-11-11
forum: Desktop Environments
---

### Post by blaze042 on 2007-11-11
Well, I'm at a loss right now. What I'm trying to accomplish:

Automatically toggle KDE Sound System on/off through a shell script.

If the sound system is enabled, when I try to launch a specific program I don't get sound and I get this message:
open /dev/[sound/]dsp: Device or resource busy

However, if I disable the sound system (System Settings -> Sound System: unchecked "Enable the sound system") and start the application, the application I launch has sound.

I've tried the following in various orders:
killall artsd
artsshell terminate
Changing the appropriate attributes in knotifyrc from 'true' to 'false'.

No matter what, I'll get the message and no sound in the application.

Now, I've already trolled the forums and did searches in Google. I've exhausted my options and this message is my last resort. Are there any solutions?

---

