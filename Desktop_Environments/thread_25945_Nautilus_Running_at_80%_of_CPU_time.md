---
title: "Nautilus Running at 80% of CPU time"
date: 2005-04-11
forum: Desktop Environments
---

### Post by darthsabbath on 2005-04-11
Hi all,

Had a strange occurance last night... out of the blue, Nautilus started consuming 80+% of my CPU time, with Xorg taking up the remaining 10-15%.  This effectively kills my system, slowing it down beyond belief.  Last night even even crashed the entire system, couldn't restart X, couldn't switch consoles, nothing.  When I kill Nautilus, it simply reopens with a new PID.

To my knowledge there were no changes: all I did in my home directory was delete some downloaded files, and change the way that Nautilus displays icons (this was changed back well before the issue began).

I can't find any relevant information on Google.  I found one thread in the Ubuntu mailing list that matches the symptoms, but it was never resolved.

BTW, this only happens on one user.  Created another user, and it works fine.

If a screenshot or command line output are needed, please let me know.

The system, BTW, is running Hoary fully up to date, with an Athlon 2400+ CPU and 512 MB RAM.

UPDATE:  Well, I got home from work, tested the issue with Kubuntu, no probs.  The file manager opened fine.  Went back into Gnome and opened another directory besides home, it worked fine.  Opened home... CPU=melted slag.  So I basically started moving files... moved 4 Jpgs, with filesizes of 16.6, 44.9, 155.1, and 55.1 KB, and an MP3 of size 3 MB, then tried opening my Home directory... worked fine.  Moved the files back, it worked fine.

So I have no clue. 

Any ideas what would have caused this so I can avoid it in the future?

Thanks,
Phil

---

