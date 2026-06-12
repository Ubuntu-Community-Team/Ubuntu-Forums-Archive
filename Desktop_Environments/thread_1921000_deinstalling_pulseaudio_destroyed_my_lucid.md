---
title: "deinstalling pulseaudio destroyed my lucid"
date: 2012-02-05
forum: Desktop Environments
---

### Post by ben178 on 2012-02-05
hi!

first of all - sorry if I sound panicked.
what happened:
because of the old and well known issues with muting internal speakers when plugging in a headphone jack, this time I tried deinstalling pulseaudio and connected entries that showed up when searchin for "pulse audio" in the application manager. Someone somewhere had posted the advice.
I remember not feeling too secure of what I did, especially when prompted wether I wanted to delete some associated entry as otherwise the entry I had selected was not going to be deleted. I think it was something connecting gnome and pulse, thus maybe I would have ended up deinstalling part of (or all of?) my gnome environment.
Now, booting brings up the login screen, looking more "basic" than usual, like the theme or skin was missing; when I log in, however, only the console appears.
Can anybody help me bring back my desktop?
Sorry if I'm not specific enough, it's what I know. I'll happily add information as requested.
Might a simple system update help and fill in what I destroyed? If so, how to do that from console?
I'm not too experienced with Ubuntu still.
Using Lucid.

Thanks in advance!

---

### Post by Krytarik on 2012-02-05
First of all, reinstall the "ubuntu-desktop" meta-package, this should get you back to your desktop:
```
sudo apt-get install ubuntu-desktop
```Then, look up the log file "/var/log/apt/history.log" for anything else that might have been removed in the course and isn't reinstalled by the above step.

Regards.

---

### Post by ben178 on 2012-02-05
thanks for quick answer.
realized I'm not connecting any more (writing from other machine).
guess since the desktop's gone, so is the automatic internet login; definitely gone is the question for the keyring password that used to come up.
advice on how to go online from console?
Searched around a bit and found this
```
iwconfig <interface> essid <network name> key s:<network password>
```
here:
[http://ubuntuforums.org/showthread.php?t=1185936](http://ubuntuforums.org/showthread.php?t=1185936)
but had an error output:
```
Error for wireless request "Set Encode" (8B2A) :
      SET failed on device <device name> ; Invalid argument.
```
or should I start another thread for this?

---

### Post by ben178 on 2012-02-06
I've been able to connect via cable without any further do.
```
sudo apt-get install ubuntu-desktop
```
did it, everything seems to be working fine. some adjustments are gone, naturally.
I'll check "/var/log/apt/history.log" wether there's anything else I should have wanted to keep and guess I'll be fine.
thanks a lot!!!!

---

