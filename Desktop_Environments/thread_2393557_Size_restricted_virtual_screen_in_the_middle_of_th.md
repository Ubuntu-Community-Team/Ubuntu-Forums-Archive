---
title: "Size restricted virtual screen in the middle of the physical screen?"
date: 2018-06-05
forum: Desktop Environments
---

### Post by konstantin1 on 2018-06-05
I have a big HiDPI screen, 21.5" full HD, but it uses an old TN LED technology, viewing angle is very narrow: colours get distorted at the bottom and at the top of the display. Using only a smaller rectangle for the whole desktop in the middle of the physical screen would help with the narrow viewing angle, when I look at my monitor from a closer distance (typing, browsing, etc). When I look at my monitor from a bigger distance (watching a video), picture seems OK, however I would like to use it for other purposes too, when I am looking at it from a closer distance.

For this reason I would like to make somehow a virtual screen with a resolution 1024x768 or even below, let's say 800x600 in the middle of the physical screen, which has a native resolution of 1920x1080. So my monitor resolution would be set to its native 1920x1080, but my X desktop screen (xfce4) would occupy only an 1024x768 rectangle in the middle. Is it possible? How can I do that?

[[img]https://i.imgur.com/vymDgNC.png[/img]](https://i.imgur.com/LtUTeZp.png)

I think I sould change my /etc/X11/xorg.conf however I have no clue what sections and what keywords / parameters to apply in it. Anyway I am using a proprietary nvidia driver currently, Nvidia-96xx. Browsing the different similar questions I can only find solutions for the problem, when the virtual screen size is bigger than the actual resolution of the display, and one can pan (panning) the viewport by moving the mouse against the screen edge.

---

