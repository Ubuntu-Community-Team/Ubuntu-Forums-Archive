---
title: "I really messed up: NVIDIA failed to initialize..."
date: 2008-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by demoiselle on 2008-10-28
I think I really messed up. I've been using Ubuntu for about six months. I tried updating my Dell Inspiron 530, which came with Gutsy installed on it and which I'd already upgraded to Hardy, with Intrepid. I did it because I had been having some problems with freezing, and I thought perhaps the new version would be more stable.

Now that I've attempted to install Intrepid, when my computer starts up I get the following message:

(EE) NVIDIA (0) Failed to initialize the NVIDIA kernel module!
Please ensure
(EE) NVIDIA (0) that there is a supported NVIDIA GPU in this
system, and
(EE) NVIDIA (0) that the NVIDIA device files have been 
created properly.
(EE) NVIDIA (0) Please consult the NVIDIA README for details.
(EE) NVIDIA (0) *** Aborting ***
(EE) Scree(s) found, but none have a usable configuration.

There is a box to click OK, but the cursor is frozen.

What can I do? I'd prefer not to do a clean install from the CD of Gutsy that Dell sent with the computer. I'd lose two files that I hadn't yet backed up. I guess the last upgrade I did was so smooth, I didn't expect this...

---

### Post by demoiselle on 2008-10-28
It looks like I fixed this problem after I booted into rescue mode. I went to the root menu, and as I tried to figure out how to backup those files, ran dpkg. Now I can start my computer and although it isn't perfect, I think that once the updates are run, it'll be OK.

---

