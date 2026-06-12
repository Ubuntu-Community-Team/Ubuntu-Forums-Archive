---
title: "nautilus crashes in directories containing movie thumbnails"
date: 2008-10-12
forum: Desktop Environments
---

### Post by key on 2008-10-12
Hi All,

I've been experiencing a very reproducible crash with nautilus but have been unable to find a fix or work-around. 

Nautilus crashes if I browse directories containing movie thumbnails. The crash occurs ~1 minute after I load the directory. Nautilus will correctly create the thumbnails, if they do not exist, for all files. If I navigate to a new directory (away from the movie directory) within a short time (~30 seconds) I can avoid the crash. It does not seems to be linked to the generation of the thumbnails directly but it does not happen if I turn off the thumbnail preview. 

Anyone else seen this behavior and/or know of a fix?

---

### Post by Solomoriah on 2008-10-16
I haven't seen this behavior yet, but I'm experiencing similar behavior in folders full of pictures.  The .xsession-errors file contains nothing useful regarding the problem, just repeated startup messages from Nautilus.  It doesn't happen every time, nor does it  happen in the same folder necessarily, but it happens every few minutes while browsing our virtual "photo album" on my wife's XP computer.  So, could be an SMB problem, or a thumbnailing problem.

Anybody know how to get crash details out of Nautilus?

---

