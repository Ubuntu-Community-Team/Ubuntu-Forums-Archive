---
title: "Video on C840"
date: 2007-12-24
forum: Dell  Ubuntu Support
---

### Post by lockwoodhorn on 2007-12-24
I am totally new to Linux and I'm not sure where to go from here...

I had a black screen come up after running ENVY to install the drivers for my NVIDA GeForce4 Go 440 video card. I thought that maybe because the graphics card supports multiple monitors that it bumped over to a second monitor. I plugged in a monitor to the back of the laptop and there it was.

So my question is, how do I get it to recognize my LCD on the laptop first?
Any ideas?

Dell C840
NVIDIA GeForce4 Go 440
Ubuntu 7.04

---

### Post by woodcarver on 2007-12-26
I have the same laptop, I can't get the nVidia drivers to cooperate so I don't use them. However, I do have a nVidia card in another machine. Do you have the "tool-kit" for the card? It should have options to switch from one screen to the other.

---

### Post by jecker on 2008-04-10
I have this same laptop, I also had the same problem. The problem I found was the LCD screen was not sending the correct signal, so the video driver configured itself to use a CRT instead. I fix this problem by changing the config to use DFP (Digital Flat Panel). Once I did this everything worked great.

See my post at [http://ubuntuforums.org/showthread.php?t=698621&page=3](http://ubuntuforums.org/showthread.php?t=698621&page=3)

---

