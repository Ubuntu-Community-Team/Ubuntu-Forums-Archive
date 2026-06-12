---
title: "help! I seem to have destroyed sudo"
date: 2006-06-06
forum: Desktop Environments
---

### Post by enochb on 2006-06-06
When I updated to dapper drake it completely filled my tiny 4 gig drive... to the point that I could not add any programs or run certain ones. So I got a briliant idea to mount a  new 140 gig drive from /usr, and move all the items from that directory to the new drive. This solved my space issues... and I thought all was great until I tried to use a sudo command... and found that I no longer have access to anything that requires root access. Is there a way to fix this... or do I need to wipe it clean?

---

### Post by TrendyDark on 2006-06-06
Why not just whip out the tiny drive and install Ubuntu on the 140gig drive? You could even have your 4gig drive mount as your /home directory.

---

### Post by shamrock_uk on 2006-06-06
You'll need to do more than simply copying your files across, it's not quite *that* simple, although it's not too bad. 

Have you configured the new mount point in /etc/fstab for example?

---

### Post by enochb on 2006-06-06
I have correctly mounted the drive, and everything but sudo seems to work well.

---

### Post by enochb on 2006-06-06
My new 140 gig drive seems to have a boot sector problem... grub fails when I try to install on it.

---

