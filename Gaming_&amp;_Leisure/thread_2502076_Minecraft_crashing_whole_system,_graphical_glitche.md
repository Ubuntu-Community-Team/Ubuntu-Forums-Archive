---
title: "Minecraft crashing whole system, graphical glitches"
date: 2024-11-01
forum: Gaming &amp; Leisure
---

### Post by andreizabest on 2024-11-01
I was trying to run minecraft on Ubuntu 24.04.1 LTS however after and indeterminate amount of time after entering a map could be 10 seconds or 10 minutes the whole system crashes and I get graphical glitches, regardless of what I'm actually doing in the game. I've had a similar issue under arch hence why the video I've attached is for arch but the issue is pretty much identical in the way it looks and manifests. I have OpenJDK 21.0.4 installed. I've downloaded a somewhat demanding game and ran it at max settings on Ubuntu to test it out with no issues (The Forest). I've ran memtest86 and did a stress test in Windows with AIDA64 for about 10 minutes with no issues, and every game works fine under Windows as well including minecraft, leading me to believe it's not an issue with my system. 

I've also attached some snippets of the logs, it seems to start with minecraft re-initializing the GPU followed by various errors from varying software all regarding the graphics/display and it all ends with kernel error regarding a NULL pointer reference. 

The game briefly freezes then both screens go black, followed by both screens coming back on now with my main monitor where the game is running mirrored on to the second one and both have some graphical artifacts all over, then another black screen followed by even worse artifacting. It either stays that way or I've had it where it returns me to the login screen but nothing works, time is frozen, and all my USB peripheral devices seem to think they're disconnected. I have to hard reset the system to get it back up and running. I have no idea what causes this. 


[https://pastebin.com/0mN6wpQ0](https://pastebin.com/0mN6wpQ0)
[https://youtu.be/a-ZGy0iVfqc](https://youtu.be/a-ZGy0iVfqc)

---

### Post by nicolasdentremont on 2024-11-01
What kind of GPU do you have? The first thing I would do is make sure that my GPU driver is up to date.

---

