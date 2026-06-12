---
title: "XBMC - launcher and mednafen slow + no sound"
date: 2011-01-17
forum: Gaming &amp; Leisure
---

### Post by bedek on 2011-01-17
Hi,

I'm having hard time trying to use **mednafen** emulator from **XBMC**, few of my problems:
[B]
1) it doesn't want to run in full screen mode (yes I'm using fs 1 start parameter)
2) sound is not working
3) even if I will start it I don't how to quit it from remote[/B]

To start mednafen from I'm using [http://code.google.com/p/xbmc-launcher](http://code.google.com/p/xbmc-launcher)

When I run mednafen from Xwindows (Xubuntu) and XBMC is turned off then the game start in full screen mode (fs 1) and sound works fine, also the emulator performance is fine. Looks like XBMC is taking over the control and other apps can't work properly or not performing well.

**My questions are:**

a) is there better "Launcher" application then the one which I'm using that allows running mednafen correctly ?

b) as workaround I would like to start some "menu" before staring xbmc and give user an option to choose: Emulator OR Xbmc - is there maybe some app which can be used and controlled by remote control to do that ?

c) how can I turn off mednafen using remote control ?

---

### Post by bedek on 2011-01-18
> **bedek said:**
> Hi,

I'm having hard time trying to use **mednafen** emulator from **XBMC**, few of my problems:
[B]
1) it doesn't want to run in full screen mode (yes I'm using fs 1 start parameter)
2) sound is not working
3) even if I will start it I don't how to quit it from remote[/B]

To start mednafen from I'm using [http://code.google.com/p/xbmc-launcher](http://code.google.com/p/xbmc-launcher)

When I run mednafen from Xwindows (Xubuntu) and XBMC is turned off then the game start in full screen mode (fs 1) and sound works fine, also the emulator performance is fine. Looks like XBMC is taking over the control and other apps can't work properly or not performing well.

**My questions are:**

a) is there better "Launcher" application then the one which I'm using that allows running mednafen correctly ?

b) as workaround I would like to start some "menu" before staring xbmc and give user an option to choose: Emulator OR Xbmc - is there maybe some app which can be used and controlled by remote control to do that ?

c) how can I turn off mednafen using remote control ?

Have a look to this thread, it resolved most of the problems:
[http://forum.xbmc.org/showthread.php?p=659443#post659443](http://forum.xbmc.org/showthread.php?p=659443#post659443)

---

### Post by fornax01 on 2012-06-03
for people with sound problems i managed to get my sound working by using

 -sounddevice "sexyal-literal-default"

it forces mednafen to use the Alsa default sound device

---

