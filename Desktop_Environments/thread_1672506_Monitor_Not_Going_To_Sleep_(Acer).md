---
title: "Monitor Not Going To Sleep (Acer)"
date: 2011-01-21
forum: Desktop Environments
---

### Post by A4orce84 on 2011-01-21
Hey Everyone,

I recently installed Ubuntu 10.10 and have been very pleased with it for the past few weeks. I got a good mix of programs to use and have been very impressed with the performance and apps available.

However, my monitor (Acer x223w) refuses to go to sleep (power-saving mode). The screensaver comes on, and I have set it in the power options to go to sleep in 15 minutes, but it just stays on for hours and hours.

Anyone experience this same issue with a solution that works? Thanks in advance!

--Asif

---

### Post by A4orce84 on 2011-01-21
Ttt

---

### Post by A4orce84 on 2011-01-21
anyone?

---

### Post by Krytarik on 2011-01-22
Try to use "xscreensaver" instead of "gnome-screensaver". But, though xss seems to work more reliable generaly, it has other issues, like not always getting disabled when watching videos in fullscreen, depends on the player.

[http://ubuntuforums.org/showthread.php?t=1358946](http://ubuntuforums.org/showthread.php?t=1358946)

---

### Post by A4orce84 on 2011-01-24
Hey Krytarik,

That fixed my issue! My monitor is able to successfully suspend and go to sleep now. I have one quick question though.

_Question:_

In the link you sent me, there are directions for adding the "xscreensaver -no-splash" to the startup applications in Ubuntu. The directions specifically state, "*Find the startup application "Screensaver" and select it."

I was unable to find a "screensaver" application, and was curious if you knew where it was located? Or had a better way on how to add the xscreensaver to my startup applications?

Thanks again!

---

### Post by A4orce84 on 2011-01-24
Ttt

---

### Post by Krytarik on 2011-01-24
The guide seems to be a bit outdated in that aspect. In fact when I tried xscreensaver and opened it's preferences it asked me to start its daemon. Somehow that was enough to enable it permanent, I believe. When it doesn't asks you about to start the daemon when you open it's preferences, you don't have to anything more.

Actually I guess I don't found how each screensaver gets started. If you want to start xscreensaver through the "Startup Applications", just add a new entry for it there.

---

