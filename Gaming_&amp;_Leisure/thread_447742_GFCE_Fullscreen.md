---
title: "GFCE Fullscreen?"
date: 2007-05-18
forum: Gaming &amp; Leisure
---

### Post by thehuman on 2007-05-18
GFCE seems to be a little moody for me. I have it set to fullscreen, and sometimes it will display true fullscreen, but other other times it will display a "framed" fullscreen, with the NES screen just small and centered in the middle of the screen. Is there something I am doing that is causing it be inconsistent like this? I am using .0.6.0, and I installed it from the add/remove dialog, if that makes any difference.

Also, the frontend for the program mentions referring to the documentation for more info on command line options, but I have not been able to find any. Anyone have any info on the CL options? Thank you all many times for your help.

---

### Post by felixruina on 2007-06-08
I've never gotten gfce ultra to stretch to fill the scree, either.  However, if you add "-special 4 -specialfs 4" in the "Advanced" tab, this will effectively triple the size of the window, which helps quite a bit.  There are actually a total of 4 options for these tags: -special 1 does a low-res doubling, -special 2 does a high-res doubling, -special 3 does a low-res tripling, and -special 4 does a high-res tripling.  The -specialfs options do exactly the same thing, only for fullscreen mode.

Hope this helps!

---

