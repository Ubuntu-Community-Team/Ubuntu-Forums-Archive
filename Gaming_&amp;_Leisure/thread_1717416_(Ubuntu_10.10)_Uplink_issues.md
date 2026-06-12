---
title: "(Ubuntu 10.10) Uplink issues"
date: 2011-03-29
forum: Gaming &amp; Leisure
---

### Post by fisch246 on 2011-03-29
Uplink is currently running in windowed mode, and somewhat cut off by docky. I'm trying to make it fullscreen, but when I select the options menu nothing shows up. It just says uplink at the top, but everything else is black. So I can't reset it to fullscreen, practically making the game unplayable because apart of the screen is cut off. Is there anything I can do to fix this?

---

### Post by Inkpot on 2011-12-03
This is exactly what happened to me and now I'm stuck. This is what I get for futzing around with the options trying to make the text bigger...if anyone could help, I'd really appreciate it.

---

### Post by pieman711 on 2011-12-03
I was having an issue with the mouse not being detected at the very bottom of the screen, where the most useful buttons are. That meant I couldn't change any settings. At the time it was running in fullscreen but there was a discrepancy between game resolution and screen resolution that was causing a problem. I fixed it by opening a terminal and running
```
uplink -graphics_fullscreen
```

(Because I installed through desura I had to use...
 
```
cd /PATH TO DESURA FOLDER/common/uplink-trust-is-a-weakness 
```
And
```
 ./uplink -graphics_fullscreen
```
)
This will run it in widowed mode. If you can't see the menu buttons atthe bottom of the screen hold alt and drag the window up the screen to see anything cut off. This should allow you to access any graphic options and play with it until it works.

---

### Post by Inkpot on 2011-12-03
Wow, thanks! I love this community so much...you, sir, are completely awesome. :)

---

