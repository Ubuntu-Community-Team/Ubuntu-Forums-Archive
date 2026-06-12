---
title: "Americas Army Not working"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by ProjectWhat on 2007-04-03
I have searched and found errors somilar to min but not exact and they keep turning up bad. So this is the error I have;
```
ben@ben-ubuntu:~$ armyops
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error
ben@ben-ubuntu:~$ 
```
What does that mean?? is it something to do with the graphics card?
I have a nvidia card and ubuntu 6.10

---

### Post by Swab on 2007-04-03
I would imagine you need to install the restricted nvidia driver if you haven't already.

Try..

```
sudo apt-get install nvidia-glx
```

Then reboot and try again.

---

### Post by hikaricore on 2007-04-03
Yes you need to install the binary drivers for your nvidia card.

This may be of some help: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by ProjectWhat on 2007-04-03
Yes ok i got that fixed. Thank you. I seen somewhere that since there is no AA 2.8 for linux that 2.5 is the latest. WEll thats what i have is 2.5, but is there a special server that everybody uses for 2.5? Or is there anyway to get 2.8 for linux (Without Wine)?

---

