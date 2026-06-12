---
title: "multiple displays and ioQuake / openarena / wop / tremulous"
date: 2007-09-19
forum: Gaming &amp; Leisure
---

### Post by rybu on 2007-09-19
I'm running two displays with xinerama at present.  Most of my applications respect the display they were started in, even if they go full-screen.  But the games based on the ioQuake engine listed in the title, they all grab display 0, even if started in display 1.  Does anyone know how to reconfigure these apps to use a display other than display 0?

---

### Post by PurposeOfReason on 2007-09-19
You'll have to play with the metamodes in your xong.conf. I believe it'll look something like "NULL.1024x768" or reversed depending on which side you want to use.

---

### Post by rybu on 2007-09-20
I found a solution.  Just disable xinerama.  Added benefit is the screensaver no longer crashes.. The only downside is I can't move windows between my two displays anymore.

---

