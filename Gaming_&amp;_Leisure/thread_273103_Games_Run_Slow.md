---
title: "Games Run Slow"
date: 2006-10-07
forum: Gaming &amp; Leisure
---

### Post by christxr on 2006-10-07
I am wondering why graphic intensive games are running really slow. I know that acceleration is turned on on my nvidia 5200 but it still runs slow. Even when I turn down all the graphic bells and whistles it's jerky and sometimes hard to control. 

I am running compiz/xgl but I don't think its running when I start my session. I have to type 'compiz-start' to get the effects. How can I tell what's eating up my video memory? (Games run great with most of the higher video settings in Windows). Any ideas?

---

### Post by baldy1324 on 2006-10-07
try typing top into a console this will show processes by cpu usage.

---

### Post by aidanr on 2006-10-07
type into a terminal ```
glxinfo | grep direct
``` if direct rendering says no, then refer to this thread [http://ubuntuforums.org/showthread.php?t=176636&highlight=nonXgl](http://ubuntuforums.org/showthread.php?t=176636&highlight=nonXgl)

---

### Post by Flaringo on 2006-10-07
compiz/xgl + 3D games = false

Well, that's my opinion. Planetpenguinracer was performing bad on it, CS on steam wasn't even working, and World of Warcraft was running in about 10FPS in the menu. I removed beryl, and whoops, look at that. All of a sudden everything was running just fine!

---

### Post by christxr on 2006-10-07
Thank you very much aidanr! That did the trick. YOU ROCK!

---

