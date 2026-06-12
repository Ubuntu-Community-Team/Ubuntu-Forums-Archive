---
title: "Grub takes approximately 15 seconds to load. / Strange font resolution behavior."
date: 2006-07-20
forum: Desktop Environments
---

### Post by vf514 on 2006-07-20
In contrast to GRUB's behavior on my last hard drive, stage 1.5 loads almost instantly (it took about 1-2s previously) but actually loading GRUB takes much longer. Any ideas about how I can speed up the loading time?

Also, after a fresh install on my machine, changing the font resolution from 50 to 51 (preferences > font > details...) resulted in a dramatic decrease in font size. I use the FreeSans font. See if you can reproduce this, this may be a problem. I am not an expert on the subject, however. I am merely speculating.

---

### Post by vf514 on 2006-07-20
On my user account, the font resolution was preset at 50 dpi. However, on the root account, it is preset to 96 dpi, which appears to be the correct default setting. It appears that the reason the fonts became so much smaller is because it was simply preset to an incorrect value.

---

### Post by vf514 on 2007-01-09
This is quite an old post, but I thought I would post the reason grub started hanging, since I know what happened now; and this information may help a user that is searching the forums.

When grub started hanging, I had a hard drive on the same IDE channel as my CD-ROM drive. Removing it enabled grub to start in a regular amount of time (under one second). It appears as though grub does not function as well under such a configuration.

---

### Post by Schalken on 2007-01-10
Which was the master and slave?

---

