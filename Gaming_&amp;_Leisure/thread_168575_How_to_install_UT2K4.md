---
title: "How to install UT2K4"
date: 2006-04-30
forum: Gaming &amp; Leisure
---

### Post by gRiMgRaVy014 on 2006-04-30
I thought you just had to insert teh cds. Well  I tried that and had to luck. I tried the "play" disc and Install Disc 1 with no luck. I'm just looking for instructions to install my favorite windoze pc game.

Thanks!

---

### Post by rs3 on 2006-04-30
My experience with it was fairly simple...

I put in Installation Disc 1.  Then, I opened a terminal, copied the install script (**cp /media/cdrom/linux-install.sh .**) from the CD to /home (temporarily), switched to root (**su**), then typed **sh linux-install.sh**.

From there, it should walk you through it.

(As I recall, if you try to run **linux-install.sh** from the CD, you won't be able to unmount the discs, which is necessary for the 5 CD install :)

---

