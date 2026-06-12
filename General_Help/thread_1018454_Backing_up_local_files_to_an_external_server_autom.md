---
title: "Backing up local files to an external server automatically each night"
date: 2008-12-22
forum: General Help
---

### Post by markblue777 on 2008-12-22
Hi all, i am fairly new to ubuntu (and linux in general). However, what i am trying to achieve is backing up a local software raid1(or maybe just some key folders i need saved) to an external source (my dedicated linux box which is located off site). I need it ideally running every night (i believe i can set a process through cron to achieve this).Are there any tutorials or anything that could assist me in getting this to work. I have been looking around for some time now and cant find anything but i may just be searching for the wrong thing.
Any help much apprechiated.
Regards
Mark

---

### Post by hyper_ch on 2008-12-22
setup a passwordless ssh login for the remote computer and then use cron to rsync the desired stuff every night.

---

### Post by markblue777 on 2008-12-22
hey hyper,
Thanks for that it is just what i am looking for.
For anyone else out there here is the tutorial i found to achieve this.

[rsync link]("http://www.engadget.com/2007/03/21/how-to-automatically-back-up-your-computer/")

---

