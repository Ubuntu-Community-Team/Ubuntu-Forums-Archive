---
title: "touchpad with evdev not work"
date: 2012-09-16
forum: Desktop Environments
---

### Post by maiky123 on 2012-09-16
Hi

i have problem with my touchpad. 
i have ubuntu 12.04 64bit installed on HP Probook 4330s.
and i try to install touchegg. 

and when I add to /etc/X11/xorg.conf this
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "evdev"
        MatchIsTouchpad "on"
      MatchDevicePath "/dev/input/event*"
EndSection

```
my touchpad not work.

if I delte them or change the driver to the synaptics, touchpad works but without touchegg gestures.

what can be problem?

I have installed utouch and evdev from this page [http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/](http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/)

---

