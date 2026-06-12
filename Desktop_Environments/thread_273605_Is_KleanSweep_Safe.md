---
title: "Is KleanSweep Safe?"
date: 2006-10-08
forum: Desktop Environments
---

### Post by christxr on 2006-10-08
I was just running KleanSweep and I got the willies. Has anyone had trouble deleting files that it finds. This makes me nervous, but I really need to clean up my drive because I'm running out of space. Any advice?

---

### Post by kerry_s on 2006-10-08
Uninstall anything you don't use. 

Delete> /usr/share/doc and /usr/share/man <if you don't use them, i usally look on line for info on a app, but depending on what you installed you can get back about 200+mb there. It has to be done as root> sudo nautilus /usr/share

You can also delete some of the back up log files if you want to.> /var/log

---

### Post by ferd on 2006-10-08
My experience is don't use as root.

---

### Post by kerry_s on 2006-10-08
Okay, i tried kleansweep and i would not use it, in fact i'm uninstalling it now. It really does nothing but remove 0mb files that aren't taking any space in the first place. The risk of killing your system is also very high, i just noticed it killed synaptic, it removed a empty file in in var/cache/apt/, i guess some empty files are needed.LOL. :-|

---

### Post by christxr on 2006-10-09
Thanks much, I'm going to uninstall as well. I'm glad I asked. Looks like doing it manually is the way to go.

---

### Post by obscur156 on 2007-04-07
Same here,i have used it once and screwed my system.I had to reinstall ubuntu.If you are new to linux like me,dont use it. ](*,)

---

