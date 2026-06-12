---
title: "Xinerama - Need to Maximize across screens"
date: 2012-04-26
forum: Desktop Environments
---

### Post by zbuffered on 2012-04-26
I'm trying to get a high-resolution video to play across three 1080p monitors in portrait mode.  I'm using 2 nVidia cards and have three screens setup with xinerama.  It looks good but, whenever I maximize a window, it maximizes on only one monitor.  

I understand this is the preferred behavior for most people but it's not what I need here.

I tried this setup with a single ATI card that supports 3 monitors, and I was able to get video to maximize properly across all 3 monitors because I didn't need to use xinerama thanks to [this thread]("http://askubuntu.com/questions/73573/how-to-maximise-a-window-across-two-monitors").  

I had issues with the ATI drivers that led me to try two nVidia cards.

Can anyone help me disable this feature so I can fullscreen across my monitors?  I'm willing to try a different window manager etc.

---

### Post by zbuffered on 2012-04-26
Haven't gotten it to work yet but the solution appears to be [Fake Xinerama]("http://home.kde.org/~seli/fakexinerama/").  [Credit to alt146]("http://ubuntuforums.org/showthread.php?p=11876037#post11876037") for the solution.

---

