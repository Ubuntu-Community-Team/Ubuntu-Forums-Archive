---
title: "Various applets crash, causing total lockup"
date: 2010-05-05
forum: Desktop Environments
---

### Post by MS-Hater on 2010-05-05
This seems to be related to the time the computer is active, though I admit that it could also be the fact that I actively switch between user accounts now and then. Essentially, I get a pile-up of errors about numerous different applets that crashed, and the dialog box asks if I want to delete them from my config... also worth noting is that after the first error pops up, the hard drive activity light never goes off; like something is constantly writing to\reading from the hard drive. Once the first error pops up, the mouse stops working, the keyboard is useless, and the only way to recover from this is to pull the power plug from the PSU. If this is a known bug, then I pose the question; why was Lucid released with such a bug as this?? This is almost enough to drive me back to M$ windoze.

Comp is a stock Dell Dimension 4600I with 1GB Dual-channel RAM, if that makes any difference.

---

### Post by MS-Hater on 2010-05-06
I've done some more work trying to pin this bug down, and I've found that it's caused by a program that I used without problems under Karmic, but am now having memory issues under Lucid. The Program in question is OGGConvert 0.3.2. I've contacted the dev, and am awaiting his response, but I want to know; could this be an issue of compatibility between Ubuntu's libGTK or another dependency that's been "upgraded" with the Lucid release? If so, which one? The RAM COMPLETELY fills up, causing the crash. Any ideas\hunches? Share 'em.

---

