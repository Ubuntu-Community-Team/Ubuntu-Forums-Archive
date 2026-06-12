---
title: "Desktop effects and video"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by xRockTripodx on 2008-02-20
Ok. I originally was unable to turn on desktop effects due to my incompatible video card (the blacklisted intel chipset).  By using the "skip check", I'm able to turn on at least the basic desktop effects.  Now, when I open any kind of video file or even a music visualization, that program just shuts itself off as soon as it opens the file.  I know that was to be expected, and I've looked through a lot of forums on this without an answer, but is there a way to have both my desktop effects and video playback working at the same time?

---

### Post by adityakavoor on 2008-02-20
Its possible in Ubuntu 7.04 with Amarnath repositories for compiz fusion.

This was one main reason why is ported back to 7.04 from 7.10.

Even my card is blacklisted - intel 965 x3000

---

### Post by L815 on 2008-02-25
Yes you can watch videos with compiz enabled with the skip check, although the video quality is very blocky when enlarged from default video size.

Open up the main menu editor and enable Multimedia selector under preferences.

Under the "video" tab, change the first drop down box to 'X11'.

And if you use VLC you have to go to Settings > Video > Output (Check advanced settings), and enable X11 there too.

---

### Post by xRockTripodx on 2008-02-26
Thanks for the tip!!  I've now got VLC working great.  But where is the main menu editor?  Its not listed under my preferences or administration menus.  Do i need to have a different package installed?

---

### Post by bobbob1016 on 2008-03-01
I'm pretty sure he means to use "alacarte" press Alt+F2, and enter "alacarte" without quotes.  It doesn't require admin for me, but if it does for you for some reason, just do Alt+F2, then "gksu alacarte" without quotes, gksu is better than sudo from what I hear.

---

