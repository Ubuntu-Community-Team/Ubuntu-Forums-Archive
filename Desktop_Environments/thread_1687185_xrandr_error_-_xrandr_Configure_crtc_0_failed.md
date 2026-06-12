---
title: "xrandr error - xrandr: Configure crtc 0 failed"
date: 2011-02-13
forum: Desktop Environments
---

### Post by jakepc123 on 2011-02-13
I am trying to get Ubuntu to set the right resolution for my monitor (as I am using a VGA monitor switch box) but it does not detect the monitor and therfore limits the resolution to 800x600.

I have used xrandr -addmode to add a resolution of 1400x1050 (which is what I use on this monitor with vista)

Using
```

cvt 1400 1050
xrandr --addmode <modeline>
xrandr --addmode default 1400x1050_60.00

```
to add the correct resolution but when I try to apply it with xrandr I get the error 
```
xrandr: Configure crtc 0 failed
```  

How can I get it to let me have the correct resolution??

and keep it simple please as i'm new to Linux

---

### Post by bmxpert1 on 2011-11-18
Did you ever find a solution to this? Experiencing this same issue right now...

---

### Post by CyrusCT on 2011-12-03
I'm getting the same problem too.

I'm connecting to an HDTV and Xubuntu (11.10 amd64) isn't recognizing it's resolutions.

I connected to a computer monitor to switch to the desired mode, then changed the VGA cable back to the TV to get the correct resolution on the TV.  I then used

:~$ cvt 1280 1024
:~$ xrandr --newmode "1280x1024_Forced" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
:~$ xrandr --addmode default 1280x1024_Forced
:~$ xrandr --output default --mode 1280x1024_Forced

to capture working settings (at for the desired resolution) in my terminal history.  Unfortunately, after restarting with just the TV connected,

:~$ xrandr --newmode "1280x1024_Forced" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
:~$ xrandr --addmode default 1280x1024_Forced
:~$ xrandr --output default --mode 1280x1024_Forced

results in the "Configure crtc 0 failed" message.

I'm using an SiS 760, and using

deb [http://ppa.launchpad.net/acasagrande/xf86-video-sismedia/ubuntu](http://ppa.launchpad.net/acasagrande/xf86-video-sismedia/ubuntu) oneiric main

to install xf86-video-sismedia was only able to get me from a maximum resolution of 960x600 to a maximum resolution of 1024x768, which is still short of the 1280x1024 that my TV supports with a 63.98 horizontal freq and 60.02 vertical freq.

Any help with troubleshooting xrandr would be greatly appreciated.

Thanks, CyrusCT

---

