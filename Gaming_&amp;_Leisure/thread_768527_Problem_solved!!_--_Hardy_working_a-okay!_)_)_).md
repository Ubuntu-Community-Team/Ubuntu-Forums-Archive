---
title: "Problem solved!! -- Hardy working a-okay! :) :) :)"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-04-26
Hey A.I., it's working perfectly now, with all games :)

I now know what caused the problems and solved them with 4 mouse clicks:

During installation, my monitor was detected as an al2016wx (it is an al2016w which has a slightly lower max resolution, so this isn't completely correct, but they are apparently driver-compatible). It was set to 1680x1050, which is max res for my model, with 60 HZ refresh rate. Perfect!

However, after using restricted for nvidia driver, I saw in resolution settings  that it was set to 50 HZ, which made it chrash in 3d apps. I went to screens and graphics by typing in displayconfig-gtk in terminal (why was it removed from menu's in hardy :confused:) and manually selected al2016wx instead of plug and play monitor. Then I selected 1680 x 1050 resolution and 70 HZ refresh rate, and now everythings works :)

Victory :lolflag:

---

### Post by Perfect Storm on 2008-04-26
congrats! ^_^

---

