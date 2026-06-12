---
title: "running out of disk space..."
date: 2006-07-12
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-12
I'm starting to run out of diskspace on my ubuntu partition now that I have started using it as my primary OS (can't remember the last time I booted into windows).  So, I now have a few questions:

 - What is the best way to compress an iso?  I figure that there must be a way of compressing them so that they take up less space until I want them.

 - What is the best way to reclaim some unused space from windows?  I have about 15gb I could get from it if I ran a partition editor of some kind, though I'm not sure how this would work in practice, especially as I don't think I could merge this into my current /home directory.  I could probably get more from windows by wiping it and doing a base install, giving it about 10gb total hdd space instead of the 60gb it currently has, but that would require a fair amount of work, and I don't have too much time at the moment!

---

### Post by nkhansen on 2006-07-12
I do not know if this is the best solution, but what I did was to free the space from my windows, and make a new partition, which I mounted as /home/me/media, where I put all photos, texts and music. Not the most flexible of solutions, but it got the job done.

---

### Post by raldz on 2006-07-12
Log in to Windows and try to defrag the disk first.. then log in to Linux and use GParted to free space from your Windows partition.. then format it and mount it somewhere inside your /home folder..

---

