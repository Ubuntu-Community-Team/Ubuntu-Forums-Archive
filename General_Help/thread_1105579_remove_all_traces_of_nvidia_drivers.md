---
title: "remove all traces of nvidia drivers?"
date: 2009-03-24
forum: General Help
---

### Post by linuxisevolution on 2009-03-24
I changed kernels and my nvidia drivers got messed up. I had the drivers from nvidia.com installed so I reinstalled those once I got the new kernel. I got my resolution fixed, but I can't run any 3d apps and compiz won't enable. If I install the nvidia drivers from the repos then my resolution gets screwed up and the drivers won't work anyway. If I use the ones from nvidia's site then the same thing happens, and the same thing with nvidiang.

I am running hardy with a Geforce 8600Gt card.

I have a feeling I have to remove the traces of the old driver, how do I do this?

---

### Post by linuxisevolution on 2009-03-24
I fixed it by removing /usr/lib/nvidia and then removing all the crap Ubuntu installs for Nvidia, then ran the installer.


I HAVE COMPOSITING AGAIN! W00T!

---

