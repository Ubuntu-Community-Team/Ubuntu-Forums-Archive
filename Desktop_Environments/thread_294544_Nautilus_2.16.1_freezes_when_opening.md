---
title: "Nautilus 2.16.1 freezes when opening"
date: 2006-11-06
forum: Desktop Environments
---

### Post by Toxodont on 2006-11-06
I ran into an interesting problem today.  Here are the requirements / steps to recreate:

1) Have a large media storage folder with multiple subfolders full of pictures / movies, preferebly in the 1-2gb range at least. (in total).

2) Have some movies / pictures also stored directly on the media folders root (not just in the subfolders).

3) Open the media folder in icon mode

When I do that, my CPU spikes to 100% and nautilus completely freezes.  When I kill it, and reopen, it usually opens up multiple instances of my home folder. (around 7-10 instances).

To 'fix' this problem, I turned off image preview.  This leads me to beleive that nautilus may be trying to preview more than just the images on the current root folder, and is trying to preview all the images from the subfolders as well?

As to why nautilus opens multiple instances of my home folder after crashing is another story alltogether, which I have no idea...

Has anybody else experienced this, or something similar?

Thanks,

---

