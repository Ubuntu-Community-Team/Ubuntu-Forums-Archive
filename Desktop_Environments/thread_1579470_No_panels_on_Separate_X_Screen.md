---
title: "No panels on Separate X Screen"
date: 2010-09-21
forum: Desktop Environments
---

### Post by Ben_neB on 2010-09-21
I have my computer, which runs Ubuntu 10.04 (Second-to-newest kernel) setup with a 19" widescreen monitor and a 32" CRT TV. Now, what I want is the functionality of separate X screens. I have a Geforce 8600GT video card, and the latest drivers. And I can get TwinView to work just fine, it's just not quite what I want. 

What I;m trying to accomplish is to use my computer as a DVD player/video player for the TV, while at the same time use the computer normally without interrupting video playback. Therefore, TwinView isn't ideal, since flipping the compiz cube on my computer flips the cube on the TV too. So, I need Separate X Screens to do this correctly. 

My problem is when I enable Separate X Screens in the Nvidia settings manager, and restart the XServer, all I get on my TV is my desktop wallpaper. No panels, and I can't even right click on the TV's dekstop, or even Alt+F2 to run a command. It's as if the second screen is just disabled.

Now what's frustrating is that I had it working perfectly before I ran a bunch of updates. I was a little behind on my updates, so I don't know how many kernel updates I applied all at once last weekend when I finally got around to installing all my updates. I've tried reverting to the oldest kernel that was available in grub.cfg, thinking that may have been the culprit, but that doesn't fix it. 

Is there a way to use older kernels than I have in my /boot folder? Or is that not even a reasonable thing to suspect? Any other suggestions?

---

### Post by waperboy on 2010-12-29
Having the same issue - I got around it by disabling "Desktop Cube", and then restarting X.

Desktop Cube breaks the display of the second screen. It is really still there though, just nod displaying anything - I could create folders blindly by right-clicking and pretend I saw the menu. After disabling Cube and restarting, I saw the folders on the desktop.

---

