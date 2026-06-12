---
title: "Audio/Gamepad issues"
date: 2013-03-04
forum: Emulators
---

### Post by Xenoverse on 2013-03-04
So I have a few minor problems with my emulators. I'm running Ubuntu 12.10 x64 with Mednafen and Project64 (via Wine for the latter). I'm quite new to Ubuntu/Linux so forgive me if I'm not clear with my explanations.

Firstly, I'm using Mednafen for NES games and they all work great except I can't get any audio from any of them. When I launch a game I get [FONT=courier new]Using "ALSA" audio driver with device "default"[/FONT]. I tried [FONT=courier new]sexyal-literal-default[/FONT] but it doesn't seem to have done anything. Also, if I try to fullscreen any of these games the dimensions are all screwed up so half the game is off-screen and part of the screen is jumbled noise, and when I try to exit fullscreen, my desktop resolution is changed so that I'm only seeing a quarter of my desktop. I can't see the system settings when it's like this, so I'm forced to logout/login to reset it. I could honestly care less about the audio (unless someone knows a relatively quick fix), but is there a way to get the fullscreen to work properly?

As for Project64, the games appear to run fine except the audio is VERY choppy/glitchy. I tried all the different plugins and installed directx9 using [FONT=courier new]winetricks d3dx9[/FONT] but all gave the same result. It also doesn't recognize my controller (Logitech F310), which seems odd as it works fine when I use it for anything else (PJ64 on Windows partition, Mednafen, SuperTuxKart, etc). Again, I tried all the different combinations of plugins and the X/D switch on the bottom of the controller.

**EDIT**: Ok so after switching to N-Rage's DirectInput plugin and [FONT=courier new]sudo apt-get install jstest-gtk [/FONT]I got my controller working with PJ64. I also installed glN64 0.4.1 in an attempt to fix some dodgy graphics, but now if I try to open a ROM I get a message saying "Win32 Exception 0x80000101" and have to force quit.**** I can just switch back to Jabo's but as I said the graphics are sketchy at best.

---

### Post by Xenoverse on 2013-03-05
This is the last thing keeping me from fully commiting to Ubuntu and dumping Windows, if someone could at least tell me how to start diagnosing these problems that would be awesome.

---

### Post by Xenoverse on 2013-03-06
Bump

---

