---
title: "Stupid Question"
date: 2008-02-20
forum: Gaming &amp; Leisure
---

### Post by nsimeone2000 on 2008-02-20
What game controller (if any) is compatible with Linux/Ubuntu 7.04?

I am thinking of buying one to play game emulators and what not.

---

### Post by eilu on 2008-02-20
I think they all do.
I've used a microsoft sidewinder and it runs well.
Don't have much experience on other controllers- it's hard to pretend to work when you're holding a gamepad. :lol:

---

### Post by acoustibop on 2008-02-20
All the USB controllers I've tried (Logitech RumblePad 2, Logitech Dual Action, Gravis Gamepad Pro, several no-name Playstation-style controllers, a Playstation controller connected with a no-name adapter) have been recognised and installed automatically, nsimeone2000.

The only one I had to do some work to install was a gameport Gravis Gamepad Pro.  But that was fine once I got it sorted: I installed it using [this howto]("http://ubuntuforums.org/showthread.php?t=338457").

However, a word of warning: there are two joystick calibrators in the repositories: jscalibrator and joystick.  Joystick installs 2 command line utilities, jstest and jscal, which work fine - but of course, there's no GUI.  So a lot of people go for jscalibrator, which has a GUI - big mistake.  It has a nasty habit of messing up the directional controls on controllers, while still reporting them as working correctly.

You shouldn't really need a calibrator for a USB pad anyway, unless you need to find out how each control is configured - jstest will do that.

---

### Post by nsimeone2000 on 2008-02-20
Sweet thanks, I just have to figure out how to get my USB devices to work now:)

I don't like GUI stuff, so far I prefer terminal (I feel like I have more control that way)

I will get me a controller soon.

---

