---
title: "Keyboard Shortcuts not working"
date: 2013-05-03
forum: Desktop Environments
---

### Post by manco1911 on 2013-05-03
Hi guys. 

Im having some problems with the default keyboard shortcuts on my box, currently running Ubuntu 12.04 fully updated. 
The issue is that some of the shortcuts work.. and some dont. For example, volume up, down and mute are not working.. (special keyboard media keys), but play/pause, next and back are working fine. 
Lock screen is not working.. not even if i change the default configuration to another.. and not even generating a custom shortcut to "gnome-screensaver-command -l"

Keyboard is detected fine:
```
$ lsusb 
Bus 002 Device 002: ID 0bc2:3300 Seagate RSS LLC 
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And the keys are also working ok. 

```
$ sudo showkey 
press any key (program terminates 10s after last keypress)...
keycode 115 press
keycode 115 release
keycode 113 press
keycode 113 release
keycode  29 press
keycode  29 press
keycode  29 press
keycode  29 press
```

Anyone with thoughts ?

---

### Post by hil4vitkutin on 2013-05-05
Hello,

I'm answering with a little knowledge from this area, but my laptop's media keys (I don't have the same laptop as you do) just started working after just upgrading to a newer distribution. You seem to be using Ubuntu 10.04, so it's pretty probable that the media keys would work better in newer distros. Kernel issue I think.

Do you have a particular reason why you are using 10.04?

Sorry for not posting any solutions here :/

---

