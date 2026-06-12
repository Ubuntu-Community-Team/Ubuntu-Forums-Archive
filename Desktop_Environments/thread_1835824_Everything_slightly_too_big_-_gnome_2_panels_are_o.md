---
title: "Everything slightly too big - gnome 2 panels are off screen?"
date: 2011-08-30
forum: Desktop Environments
---

### Post by boandmichele on 2011-08-30
I am not sure how else do describe this.  nVidia GT430 hooked to a HDTV via HDMI.  It worked fine until I just reinstalled 10.10 (11.04 locked up every 30 minutes).  

After the reinstall, everything is working fine.  The resolution even looks fine.  Only problem is that it seems that things are slightly too large for the screen....or something.  The top and bottom panels are off screen, but I can still blindly click them.  They are just barely off screen, and if I bring them to 40px via Properties, I can see them in double size.  

Any ideas?

---

### Post by xdominex on 2011-08-30
Is this a desktop or a laptop that you are using?

---

### Post by jfed on 2011-08-31
Sounds like a resolution issue. Try changing the rez to your monitors, and if that doesn't work, or if you don't know it, just change it to each one listed until you find one that you like.:lolflag:

---

### Post by mcduck on 2011-08-31
Actually that's more likely to be an issue with the TV's settings. Make sure it's set to pixel-per-pixel mode (what this mode is actually called depends on the TV's manufacturer). Normal HDTV modes tend to have a bit of overscan and also might scale the image a bit which would make it more or less blurry.

The resolution could be a problem as well, more likely if it's a HD-Ready instead of Full-HD in which case you'll usually want to set your computer to 1366x768 (or 1360x768) instead of the 720p HDTV resolution, as most HD-Ready TV's actually have 1366x768 panel instead of 1280x720.

---

### Post by Gremlyn1 on 2011-10-01
I'm running 11.10 and seem to be having the same problem when running HDMI to my TV. My TV says Full-HD, and I don't see any settings in the TV's menu to change to anything resembling a 'per-pixel-mode'.

Also, the system is detecting my monitor as a Sony 52" when in reality it is a 42" LG.

---

### Post by Gremlyn1 on 2011-10-03
> **Gremlyn1 said:**
> I'm running 11.10 and seem to be having the same problem when running HDMI to my TV. My TV says Full-HD, and I don't see any settings in the TV's menu to change to anything resembling a 'per-pixel-mode'.

Also, the system is detecting my monitor as a Sony 52" when in reality it is a 42" LG.

I did some research on my specific brand TV, and found the answer I was looking for right here: [http://www.tomshardware.com/forum/51226-4-hdtv-computer-monitor-questions](http://www.tomshardware.com/forum/51226-4-hdtv-computer-monitor-questions)

Good tip for those out there that run into anything similar in the future: your TV probably has one or more HDMI/DVI ports (instead of just HDMI), which can be used for PC monitor connections as well and these are the port you need to use. In the case of my TV, I had to designate the HDMI port as 'PC' for it to recognise the appropriate resolution.

---

