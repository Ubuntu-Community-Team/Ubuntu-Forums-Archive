---
title: "newbie question - how to use locate to find something containings two words?"
date: 2005-12-07
forum: General Help
---

### Post by sup on 2005-12-07
Huh, it may sound stupid but since I am new to linux, I do not know the proper way around. I wanted to find config files of a user for krusader using locate so that I could transfer these config files to another user. I found the meventually by other means, but I was not able to figure out a wayhow to do it wioth locate (whic would be much more easier). A possibility seems to be ```
locate -r regular expressions 
```, but since I do not know anything about regular expressions (and if they can be used for it, besides, I do not know if they are installed on my system since man regexp does not work, although i found this man page in the net), I wander if there is a simple way to do this?

---

### Post by aysiu on 2005-12-07
I just tried it out on my own system, looking for a folder called "Job Search" (two separate words). ```
locate Job
``` found it...

---

### Post by speedman on 2005-12-07
locate -i word1|grep -i word2


Regards,

SM

---

### Post by sup on 2005-12-10
thanks, works like a charm...

---

