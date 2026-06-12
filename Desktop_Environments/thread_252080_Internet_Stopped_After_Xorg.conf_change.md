---
title: "Internet Stopped After Xorg.conf change?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by beetee2 on 2006-09-06
Last night I was attempting to get ubuntu lts to detect my nvidia 7600 gt. I hadn't thought the os was acting quite right since I installed, the graphics were choppy and whatnot (using xgl / compiz) and they shouldn't have been at all w/ a 7600.  

So I went into xorg.conf and change "nv" to "nvidia" in hopes it would detect my vid card.  I did a mv xorg.conf /etc/x11/ and thought things would be good to go.  

The graphics DID seem smoother after i overwrote the file, but when I tried to display the graphics card it said the same thing "default device" was detected.  

So I restarted, hit ctrl+alt+bckspce.  THEN when I loaded ubuntu, the internet wasn't working??? It has been working previously, worked right off the initial install. *scratches head* I have no idea what change would have caused that. After that, I rebooted into XP to see if it was my router (linksys wrt54g), and the internet worked fine there.  So I rebooted to go back to ubuntu, and ubuntu wouldn't even load, gave me some error about xgl not being able to start, and said for me to go into failsafe mode? Anyone have any ideas about what would've caused this?

---

