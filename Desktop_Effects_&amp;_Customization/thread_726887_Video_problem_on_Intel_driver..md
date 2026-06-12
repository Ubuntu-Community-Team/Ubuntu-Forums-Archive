---
title: "Video problem on Intel driver."
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by Dave_Connor on 2008-03-17
Just got my new desktop working and all but with video output models is funky. On open Gl on VLC Player is really weird and trys to redraw the video on multiple spots on the screen. With Xv it just crashes all together I have compiz disabled but is there a way to run Compiz and have video support ?

---

### Post by notwen on 2008-03-17
What Intel video controller do you have?  If you have the 965GM, the following solution may help you out.  Try changing your video output in your video application to 'no XV'.  I use Compiz-Fusion and bypass the blacklist, disabling my video playback.  I re-enabled it by changing my video output in VLC(my preferred video app).  Hope this helps.  =]

---

### Post by Dave_Connor on 2008-03-17
Intel Corporation 82G35 Express Integrated. On the lspci command.

---

### Post by Dave_Connor on 2008-03-22
I know I am not suppose to bump but please I need an answer to this problem.

---

