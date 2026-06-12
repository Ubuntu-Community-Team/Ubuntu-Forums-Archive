---
title: "HELP-- Dell Laptop w/ NVIDIA Graphics and External Monitor"
date: 2008-01-07
forum: Dell  Ubuntu Support
---

### Post by spivak.d on 2008-01-07
Hi all,

I just switched over to a Dell XPS M1330 laptop with NVIDIA graphics and have run into a really strange issue related to dual monitors (the XPS M1330 is 1280x800 and the external monitor is 1400x900). 

Basically, I want (and have done in the past, with a Toshiba laptop) to set up my system so that, if the computer starts up with the laptop closed and the VGA cable plugged in, it will keep the laptop's LCD off, which would allow it to correctly start on the external monitor. At the same time, if I start up the system without the VGA plugged in, the system should assume the laptop's LCD is being used and start that way. 

Instead of this behavior, though, the Dell, even if started closed and with the VGA plugged in, keeps the LCD on all the time. I used nvidia-settings to set it up this way in the past and the laptop's display knew to stay off when the lid was closed, so I'm sort of confused here. For the record, if I do open up the lid, the laptop's LCD only shows part of the screen. I just want it to say "If X, start up on external only; if Y, start up with laptop's LCD only."

Please help-- this, along with a recent illness, is getting me down way more than it should :).

-Dima

---

### Post by m94mni on 2008-01-07
I use (in xorg.conf)

        Option          "UseDisplayDevice" "DFP-2"

To have my M1710 always use the DVI port when something is plugged in there. VGA would be

        Option          "UseDisplayDevice" "CRT"

Might be worth a try.

---

### Post by spivak.d on 2008-01-07
Thanks so much! That did it!

Now for a more trivial question: If I set my Trash icon on my desktop (I enabled it and disabled the panel applet) and move it to the lower left-hand corner of the screen in the higher resolution computer, it disappears when I restart X into the lower resolution monitor. Any way to make it realize this besides just putting the bin somewhere else?

---

### Post by m94mni on 2008-01-08
Icon placement is an issue that I haven\t yet found a perfect solution for...

---

