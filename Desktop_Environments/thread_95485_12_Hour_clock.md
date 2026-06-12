---
title: "12 Hour clock"
date: 2005-11-26
forum: Desktop Environments
---

### Post by ratty on 2005-11-26
Hi, in gnome i've set my clock to 12 hours but it dosen't show am/pm on the end. My locale is set to UK so maybe this is why, how do i fix this?

---

### Post by ratty on 2005-11-27
It seems to be a locale problem, but i'm unsure how to fix it

LC_ALL=en_GB.UTF-8 date +%r

that outputs a 12 hour clock minus the am/pm, but the following works perfectly:

LC_ALL=en_US.UTF-8 date +%r

How can i modify the en_GB locale so it outputs the correct time format?

---

