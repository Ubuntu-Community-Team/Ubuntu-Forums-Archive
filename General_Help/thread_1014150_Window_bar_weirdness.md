---
title: "Window bar weirdness"
date: 2008-12-17
forum: General Help
---

### Post by rdionicio on 2008-12-17
I'm using a fresh install of Ubuntu 8.10 and I get this a lot with my window bars.

Not sure show I should go about fixing it.

---

### Post by rdionicio on 2008-12-18
bump

---

### Post by jimmy the saint on 2008-12-18
I see a funny window decoration over a windows desktop?  What exactly is your setup?  Are you using emerald or metacity to set the window decorations?  the default is metacity so if you didn't install emerald, thats what you have.

---

### Post by rdionicio on 2008-12-18
> **jimmy the saint said:**
> I see a funny window decoration over a windows desktop?  What exactly is your setup?

It's a fresh install. I haven't added anything to change Ubuntu visually. That's my mplayer window and you can see that mplayer is cut off with something on top of it.

It happens to all my windows.

---

### Post by jimmy the saint on 2008-12-18
Try a different theme.  Sometimes certain themes don't play nicely with all applications.  OpenOffice has had a lot of issues where window decorations are messed up when it is running.  There have also been several bug reports about window decoration glitches relating to nvidia's drivers in Ubuntu.

---

### Post by rdionicio on 2008-12-18
I'll give it a shot and see what happens.

Thanks Jimmy

---

### Post by rdionicio on 2008-12-18
Changed it real quick from Human to Human-Clearlooks and got the same problem. So I then changed it to Glossy and I haven't gotten the same issue yet.

Weird theme issue.

---

### Post by Merkaba_ZA on 2009-02-07
Its connected to an issue in the older drivers for Nvidia ([bug report]("https://bugs.launchpad.net/bugs/186382") on Launchpad).  I updated to nvidia-glx-180 in the repos and problem solved.  Hope it helps.

---

