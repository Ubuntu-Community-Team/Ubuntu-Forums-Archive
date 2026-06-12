---
title: "Microphone is always muted"
date: 2009-06-15
forum: General Help
---

### Post by oohnirav on 2009-06-15
I'm new to all Linux, so forgive me if I come of as ignorant or naive in any of my explanations. I'm running the main version of Linux Mint 7: Gloria on an HP Pavilion dv9700 (which uses Ubuntu, I believe), and I'm having trouble getting my internal microphone to work. I've read plenty of guides that tell you to:

1) Open volume control
2) Check everything in preferences
3) Un-mute everything in the Playback tab (there are no microphone icons under internal, external, or docking mics. There are just speaker icons)
4) Un-mute the microphone icon under the "recordings" tab labeled digital.

This is where I find the problem to be. When I close the Volume control and re-open it, the microphone under the recording tab is muted. It seems that my microphone just is not recognized by this distro, and I don't know what I can do about it.

I've been looking for help on this for a while now, and nothing has worked. If anyone can suggest anything to get my microphone working, it would be greatly appreciated. (I need my mic for Skype, and I believe this is the last thing that is keeping me on Windows)

---

### Post by MyR on 2009-06-18
I read in a blog post that linux-backports-modules-generic will fix sound problems on ubuntu for that notebook. You may have to enable backports.
Good luck!

peace

---

### Post by oohnirav on 2009-06-18
MyR, thanks for the suggestion, but I don't think it worked. Recently, I re-installed my OS in case I had messed something up. My microphone still isn't working, so I tried your suggestion. 

I went to my package manager and installed two different:
linux-backports-modules-jaun 2.6.28.11.15's

After restarting, nothing appears to have changed. :(

---

