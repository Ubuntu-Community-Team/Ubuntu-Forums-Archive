---
title: "nvidia and sound issue"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by draeath on 2007-03-24
Hi, I've recently put together this machine, and I'm noticing a VERY strange problem...

The issue: when running an OpenGL application in fullscreen mode (windowed, even at my full screen size - is fine) the sound will cut out in a regular pattern... it sounds like I have a 1/4 second of silence for every 1/4 second of sound. It doesn't appear to be falling very far behind however. The video seems to be running fine. This appears to happen with ALL OpenGL applications, and also DirectDraw applications running in WINE in fullscreen.

I'm running Kubuntu 6.10, i386. I have a pentium D 805 (2 core, 64b, but i have 32 bit kernel and userspace) with 1024mb pc3200, the system also has 2gb of swap.

I have a GeForce FX 5500, AGP8x, 256mb. I am using the binary nvidia drivers from the repositories.

My sound card is an external SB Live 24-bit using the snd-usb-audio driver. Note that I never have had problems like this on other machines using this exact peice of hardware... windows, linux, or BSD. However I can unplug it and enable my built-in AC'97 (realtek) in my BIOS for testing.

Also note that I appear to have no issues from within windows, so I honestly don't think it's a hardware problem.

Assuming it is not the sound card, where should I start looking? Please let me know If I need to clarify, explain, or give more info about anything.

---

### Post by draeath on 2007-03-24
I fixed it... the onboard AC'97 audio does not suffer this problem.

The next step is... How can I figure out what is causing it so I can file a report to the right folks?

---

