---
title: "[SOLVED] DosBox Quake No Sound - Here is the solution"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-15
Edit dosbox.conf and set GUS=false.

---

### Post by DoktorSeven on 2008-03-15
Or go to [http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/) and grab the Darkplaces Quake1 engine that runs natively in Linux.

It runs faster and is much easier to get everything working.  (Check the Readme link and scroll down to near the bottom for install instructions -- "How to install Quake on Linux".)

---

### Post by bengoza on 2008-05-11
> **Rytron said:**
> Edit dosbox.conf and set GUS=false.
Where is dosbox.conf?

---

### Post by Rytron on 2008-05-12
> **bengoza said:**
> Where is dosbox.conf?

Hi,
Try your home folder.

Terminal:
```
cd /home/yourusername
```

If you cant find it there, tell me and I will solve the problem.
Cheers.

---

### Post by Sleaka J on 2008-05-12
> **bengoza said:**
> Where is dosbox.conf?

You won't have the dosbox.conf file unless you do the following:

"config -writeconf dosbox.conf" inside of DOSBox (no quotes). Only then will the dosbox.conf file exist in your home directory.

---

### Post by bengoza on 2008-05-15
Wow, thanks everyone! Gotta love the Ubuntu community.

---

