---
title: "White screen after booting"
date: 2006-09-13
forum: Desktop Environments
---

### Post by mcuerdo on 2006-09-13
Hi!

After booting I see a the brown screen and the clock, normally after that it should appear the login screen but I get the white one and system hangs :-? . I don't know where to look to find the clue (logs, error messages, etc...) Can you give me hand?

thks

---

### Post by bswilson on 2006-09-13
It sounds like you may have a problem with your GUI configuration (X.org).  I recommend you look for errors in the file **/var/log/Xorg.0.log**.  That file should have any problems with your XWindows configuration.  Based on what that error log shows, there could be a few things you need to try in order to fix the problem.

---

### Post by mcuerdo on 2006-09-16
I attached the file, I see some errors at the very end of it but I don't know what they mean.

---

### Post by ayoli on 2006-09-16
try this:
edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
and comment lines about wacom dev as show bellow in red:
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        [COLOR="Red"]#InputDevice     "stylus" "SendCoreEvents"[/COLOR]
        InputDevice     "cursor" "SendCoreEvents"
        [COLOR="Red"]#InputDevice     "eraser" "SendCoreEvents"[/COLOR]
        InputDevice     "Synaptics Touchpad"
EndSection

```
reboot, and see if it helps.

---

### Post by mcuerdo on 2006-09-17
thanks ayoli, I tried what you told me but didn't work, finally I found the following solution inside the xorg.conf file:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It's working now!

---

