---
title: "No Sound or Mousewheel in Unreal Tournament"
date: 2008-07-20
forum: Gaming &amp; Leisure
---

### Post by ph4zon on 2008-07-20
I have installed Unreal Tournament using the instructions from this page [http://www.fingel.com/ut/howtos/utonlinux.html](http://www.fingel.com/ut/howtos/utonlinux.html). All went well until I got to the sound part. Without following the audio instructions on that page, I get sound however it's quite jittery, slow and therefore out of sync. On the other hand, if I follow the aoss instructions on there and launch the game with it, I get absolutely no sound at all. Here are what I believe to be the relevant output lines when the game loads:

> Bound to ALAudio.so
open /dev/dsp: Invalid argument
Audio initialization failed.

I don't quite understand what the problem is as I'm somewhat new to Ubuntu, I've been using it for a couple months now. I'm running Ubuntu 8.04.1 on a Dell Inspiron 1520, on my invoice it has this listed as the sound card "High Definition Audio 2.0". My sound works fine on anything else.


Secondly, I can't get the game to recognize my my mousewheel (scrolling only, pressing it works fine). This is quite annoying, as I am used to switching weapons with it when playing under Windows. I'm using a Logitech MX510. Scrolling works everywhere else. Here's my mouse section from xorg.conf

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Button"	"7"
	Option		"ZAxisMapping"	"6 7"
	Option		"Resolution"	"100"
EndSection

I hope someone can help me out with these problems, thanks for your time :)

---

