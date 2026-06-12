---
title: "Strange graphic in Warcaft III"
date: 2007-07-02
forum: Gaming &amp; Leisure
---

### Post by Pitel on 2007-07-02
Hi, I have problem with graphic in Warcraft II. It looks like the attachement. I've wine 0.9.40 (but it looks like this since 37 as I remember), Ubuntu Feisty, and Intel 945GM/GMS/940GML. Any idea how to make easy fix? (Of course I'm using -opengl switch.)

---

### Post by almkglor on 2007-07-02
I'm currently having the same problem with the same video device.  It gets worse when you actually play - it seems that light shades are terribly bright and dark colors are especially dark, like everything went through a nasty high-contrast filter.

Turning off opengl makes it look better (not so high-contrast) but makes the game run slower than molasses.

I tried switching from xorg-video-driver-i810 to xorg-video-driver-intel, but it's still the same.

This problem began for me when I upgraded from Edgy Eft to Feisty Fawn.  Wine was working perfectly for me on Eft, and the colors in WC3 were good (nasty graphics in the starting screen, with non-existent water, as well as missing parts in the unit portraits), but suddenly all sorts of weird stuff started happening when I upgraded to Feisty.

Heck, chromium's music began to be choppy on Feisty, when it was a nice beat in Eft.

Also, another, unrelated, 2d Windows game (it's completely unknown, anyway) which ran on Edgy Eft now simply crashes in Feisty.

Somehow, I suspect something wrong with the driver...

---

### Post by almkglor on 2007-07-15
bump....

---

