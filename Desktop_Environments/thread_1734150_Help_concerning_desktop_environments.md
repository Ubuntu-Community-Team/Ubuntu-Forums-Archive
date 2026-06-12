---
title: "Help concerning desktop environments"
date: 2011-04-19
forum: Desktop Environments
---

### Post by aerofly5 on 2011-04-19
I wasn't sure where to start this thread, so please redirect me to the proper area this should be posted if it is inappropriately placed.

I am a heavy gamer, but my specs are rather terrible and I do not have the funds required to buy decent parts, so I was wondering if there were any extreme lightweight desktop environments (preferably from a repository, but source building is an option) that I could use to improve in game performance. Also any speed tweaks would be greatly appreciated. I use ubuntu 11.04 w/ all latest updates in conjunction with the fluxbox desktop environment.

My specs are:
nVidia GeForce 210 (Asus's EN210 silent model)
Pentium Dual Core E2160 over-clocked from 1.8GHz to 2GHz
2GB DDR2 ram (FSB over-clocked by 2x multiplier)


***EDIT***
I forgot to mention window managers (which I think fluxbox is). I am not sure what a window manager is, but if its the thing I'm looking for, then please let me know

---

### Post by ankspo71 on 2011-04-20
Hi,
I don't think other window managers can get much lighter than what fluxbox already is. If there are any lighter than fluxbox, I think the difference would only be slight. If you installed fluxbox in your full Ubuntu install, turn off any unnecessary services and startup applications in Ubuntu before logging into fluxbox. Installing the application called Boot Up Manger (BUM) can help disable some of the services in Ubuntu.

See the "swappiness" section on this page:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
This will help avoid poor/sluggish performance due to swap usage (if any).

Here is how you can fine tune your file ext4 filesystem:
[http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)
(It is recommended to make these adjustments from a live cd).

---

