---
title: "Can the slow speed of SDL be fixed?"
date: 2007-04-06
forum: Gaming &amp; Leisure
---

### Post by GMWeezel on 2007-04-06
Whenever I run an SDL application in Linux, they usually chug and yet I run them fine on Windows. I have an nVidia GeForce 7300 GT with the proprietary drivers installed. While searching the forums, I came across the following posts with people that are experiencing the same problem as myself:

> [http://ubuntuforums.org/showthread.php?t=202073&highlight=slow+sdl](http://ubuntuforums.org/showthread.php?t=202073&highlight=slow+sdl)
[http://ubuntuforums.org/showthread.php?t=202073&highlight=slow+sdl](http://ubuntuforums.org/showthread.php?t=202073&highlight=slow+sdl)

The first post seems to explain the problem but not what I need; the solution. My system specs are as follows:

nVidia GeForce 7300 GT
3.06 GHz HT Pentium IV Processor
Sound Blaster 5.1 Live!
512 MB RAM
Ubuntu Edgy Eft

---

### Post by GMWeezel on 2007-04-06
Bump

---

### Post by PurplePenguin on 2007-04-06
You aren't going to bump this every 45 minutes are you?  Why don't you wait a couple days and see what happens?

---

### Post by GMWeezel on 2007-04-09
bump; been long enough?

---

### Post by DoktorSeven on 2007-04-09
Programs that run SDL *only* do not have the benefit of hardware accelerated onscreen drawing in Linux.  SDL in Windows uses DirectX to implement itself, which can take advantage of acceleration.

Programs need to use SDL + OpenGL to run fast.  This isn't something that can easily be fixed; the program itself has to be rewritten/modified to use OpenGL.

---

