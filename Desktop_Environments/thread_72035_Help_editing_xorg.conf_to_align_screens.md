---
title: "Help editing xorg.conf to align screens"
date: 2005-10-05
forum: Desktop Environments
---

### Post by randomc0de on 2005-10-05
So I have a dual head setup on my Nvidia card using Twinview. Right screen is a 1280x1024 LCD, left is a 1024x768 CRT. The bottoms are aligned ok, but the top of the CRT is about 2 inches below the top of the LCD. So my problem is that when I move the mouse, or have a window straddle the screens, the CRT window is way lower than the LCD window. In other words, it's aligning it to the top, when I want the bottoms aligned. I've tried editing xorg.conf to have 

"Primary Screen" Relative "Secondary Screen" x y

With many different settings for x and y, and swapping the screens. Nothing seems to change the actual alignment, it's like I didn't even change anything.

Any hints on this one?

---

### Post by ngms27 on 2005-10-05
I think with Twinview you have to have the same resolutions.

Maybe Zinerama is what you want?

JonnyT

---

### Post by randomc0de on 2005-10-05
From my limited knowledge, Twinview is faster than Xinerama. I was hoping to run Cedega and a few games. Guess I can't be picky, so I'll try Xinerama with both screens at different resolutions. Follow-up question - anyone know how to assign one screen as the "primary"? My login currently comes up on the smaller CRT and I want the big LCD to be the main monitor.

---

