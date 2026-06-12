---
title: "krusader rootmode crash on kubuntu 6.06"
date: 2006-10-02
forum: Desktop Environments
---

### Post by jeroen2 on 2006-10-02
Hello,

I recently installed kubuntu dapper. I used automatix to install krusader 1.70. Usermode worked fine, but when I use rootmode, krusader gives an error:

```
Could not find mime type
application/octet-stream

```

and crashes. The problem has been posted to the krusader forums at: 
[http://krusader.sourceforge.net/phpBB/viewtopic.php?t=1512&start=0&postdays=0&postorder=asc&highlight=]("http://krusader.sourceforge.net/phpBB/viewtopic.php?t=1512&start=0&postdays=0&postorder=asc&highlight=")

The Krusader people first thought it was a krusader+gnome problem (kde libraries needed). Then they claimed it was a KDE problem, but their solution doens't work on kubuntu. So now the krusader folks say it's a distro specific problem. 

I temporarily fixed the problem by editing the krusader rootmode menu item, so that the command has "kdesu" before it AND the box is checked to have it executed as root (only one of these doesn't do the trick). 


So, what's going wrong in this case?


Thanks for your time,

Jeroen

---

### Post by jeroen2 on 2006-10-03
Maybe I should file this as a bug? Where do I file bugs for kubuntu?


~Jeroen

---

### Post by carla on 2007-03-26
I was having the same issue. Just fixed it with a tweak.

KMenu > Run Command... > Type in "KMenuEdit".

Find the Root Krusader entry, and change one thing: at the front of the open commands, add *kdesu. *For example, my *Command:* form data in KMenuEdit for the root version of Krusader is now:
```
kdesu krusader -caption "%c" %i %m
```

When the root version started up from that altered menu setting, it welcomed me with the "first time you've run Krusader" setup/confirmation, and then Root Krusader opened with no problem.

Hope this works for you!

---

