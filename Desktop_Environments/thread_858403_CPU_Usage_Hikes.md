---
title: "CPU Usage Hikes"
date: 2008-07-13
forum: Desktop Environments
---

### Post by Izek on 2008-07-13
Ubuntu has some serious CPU Hikes every now and then. I have a Pentium 4, HT Enabled 3.03 GHz CPU, and this causes Ubuntu to slow considerably. I have about 1.7 GB of RAM to boast as well. Is there any way to stop such huge hikes?

I know that flash in Firefox causes the most problems (even on Windows, causing hikes for Firefox 3 to go over 80% alone, and that's if you can get pass its annoying 70+ MB memory usage)

Is there another distribution that's lighter weight but without such issues? I tried Xubuntu, but it has the same problems in version 8.04.

---

### Post by tech0007 on 2008-07-13
Run 'top' to know which program is causing the cpu spike. Then use 'killall' to terminate it.

As for your next question, check this link [http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

---

### Post by mirchichamu on 2008-07-13
I was having the same problem. Somebody advised me to install and try xubantu. I did and I am happy with that untill now. If you want refer to this link:
[http://ubuntuforums.org/showthread.php?t=855572](http://ubuntuforums.org/showthread.php?t=855572)

---

### Post by Izek on 2008-07-13
> **mirchichamu said:**
> I was having the same problem. Somebody advised me to install and try xubantu. I did and I am happy with that untill now. If you want refer to this link:
[http://ubuntuforums.org/showthread.php?t=855572](http://ubuntuforums.org/showthread.php?t=855572)

I already said in my post that Xubuntu does a similar thing. =/

---

### Post by Izek on 2008-07-13
Aaand since I can't delete my posts, a little update:

Seems X.org was the culprit.

---

