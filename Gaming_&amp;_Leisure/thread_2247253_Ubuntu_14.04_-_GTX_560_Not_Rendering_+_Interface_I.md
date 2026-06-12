---
title: "Ubuntu 14.04 - GTX 560 Not Rendering + Interface Issues"
date: 2014-10-06
forum: Gaming &amp; Leisure
---

### Post by Micah_Cerrone on 2014-10-06
I'll admit that I'm new to Linux, but I've never had problems like these in the past. Keep in mind that before I installed Ubuntu, I made sure that my parts were compatible. Also, before you ask, yes, all my drivers are up to date.

PC Parts: [http://pcpartpicker.com/user/laserpigofdoom/saved/CBBv6h](http://pcpartpicker.com/user/laserpigofdoom/saved/CBBv6h)

Anyway, the main issue here is that Ubuntu refuses to allow me to use the GTX 560s to render anything. They're pretty much really expensive HDMI adapters. The load is always pinned at between 0 and 5% and even in a game as simple as Minecraft (and pretty much any other, including things like SNES emulators) my frame rate is always 20 FPS or lower, as if it was locked to that. Aside from my GPUs not working correctly, I've been having a great deal of trouble with the interface. Mainly, this being the fact that 95% of the time it refuses to let me switch between/out of windows without closing the one I'm in. I'm pretty much stuck with this until I get my paycheck (for a copy of Windows), and I work from home so... Yeah.

Thanks in advance.

---

### Post by R33D3M33R on 2014-10-07
Did you turn off the IGP from BIOS? Also, SLI might not work on Linux at all, so try disabling one card. What is the output of the command glxinfo?

---

### Post by Micah_Cerrone on 2014-10-09
I've tried using it with a single card, but no such luck. I'm about to give turning off my integrated graphics a shot. When I tried Glxinfo, all I got was something that I believe to be far from the norm. First, it gave me dozens of lines (easily clogging the terminal) all stating numbers, followed by several, spaced out, 0s, with either "true" or "false" at the end of the line. After about 45 seconds of it sitting like this, it started back up again, infinitely spamming me with numbers of increasing size with "cannot find program" (or something like it) at the end of each line. This is all very confusing.

---

### Post by dannyboy79 on 2014-10-11
which nvidia driver are you using? sounds like you didn't install the proprietary nvidia driver.

---

