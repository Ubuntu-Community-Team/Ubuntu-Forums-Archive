---
title: "LCDProc package included LCDd but not lcdproc client?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by BagOBones on 2006-09-15
I have been trying to get LCDProc up and going but it is driving me nuts. I used apt-get install lcdproc to install it but it seems like only the server got installed, not the client which actually gathers the stats.


Anyone else played around with this? It is driving me nuts.

---

### Post by Luvis8 on 2006-09-15
Hi BagOBones,
I'm having the same problem.
I think everything installed okay (I tried the newer version LCDproc 0.5.0), but I can't figure out how the heck to find this program on my computer, much less start it.
If you, or anyone else for that matter, has figured out this problem please let me know as I would really appreciate it.

---

### Post by BagOBones on 2006-09-16
Looks like the client is a script and has to be run using ./lcdproc I found it in the sources package.. Not sure if it is installed somewhere by the apt-get lcdproc. Seems stupid to me, and the docs are all full of holes..

Makes me sick when it is so easy to do this under windows with [http://lcdsmartie.sourceforge.net/](http://lcdsmartie.sourceforge.net/)

---

### Post by BagOBones on 2006-09-17
Ok got fed up with lcdproc.. found a MUCH better document project called lcd4linux.

I suggest anyone having trouble with LCDproc dump it an check out [http://ssl.bulix.org/projects/lcd4linux/](http://ssl.bulix.org/projects/lcd4linux/) it simply works and you can install it easy through the package manager.

---

