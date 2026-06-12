---
title: "Disabling Tapping with Touchpad Permanently"
date: 2011-12-01
forum: Desktop Environments
---

### Post by mamamia88 on 2011-12-01
I started out with unity and decided to use xfce instead.   The problem is that I couldn't find a way to turn off tapping with the touchpad.  I finally figured it out using a program called gpointing device settings.  But, the problem is that when I reboot even though the box to disable tapping remains checked tapping is renabled.  I uncheck it and recheck it and it's back to normal but it's really annoying to have to do this all the time.  Can anyone help?

---

### Post by LewisTM on 2011-12-01
Assuming you have a Synaptics touchpad, add a startup item with the command:
```
synclient TapButton1=0 TapButton2=0 TapButton3=0
```
Try it before in a terminal to make sure it works.

Cheers!

---

### Post by Copper Bezel on 2011-12-01
Synclient settings are sometimes reset on suspend and resume. This may or may not work. Instead, edit /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf. For instance, I have this section added at the bottom:

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "SingleTapTimeout" "320"
        Option "FastTaps" "1"
EndSection
```
Obviously, these aren't the settings you want. = ) What you want instead is Option "MaxTapTime" "0".

---

### Post by mamamia88 on 2011-12-01
> **LewisTM said:**
> Assuming you have a Synaptics touchpad, add a startup item with the command:
```
synclient TapButton1=0 TapButton2=0 TapButton3=0
```
Try it before in a terminal to make sure it works.

Cheers!

Thank you works great

---

