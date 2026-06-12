---
title: "What to back up??"
date: 2009-06-05
forum: General Help
---

### Post by penguinchrissy on 2009-06-05
I've done some searching but can't find a definitive answer to this question. I have installed timevault and am wonder, what folders should I include in my snapshots?

This backup doesn't have to be of my music and videos. I want a backup so that if my computer crashes I just reinstall ubuntu and install timevault use the backup and *presto* like nothing ever happened. 

A) Is this possible? (I assume yes)

B) Is this possible with timevault? (I'm not expecting just a one click solution I just want to know I can get back to where I was from the snapshots)

C) Am I using the best/easiest program to do this?

I understand there are a lot of programs that do backups and everyone has personal prefs. but I'm kinda new to backing up and timevault just seemed to appeal to me.

---

### Post by dje on 2009-06-05
Personally i would use [SystemRescueCd]("http://www.sysresccd.org/") and partimage or use [Clonezilla]("http://www.clonezilla.org/") to image my drive, you can then restore the image and it goes right back to how it was, you cannot backup/restore on a running system however. I would only use programs such as timevault for backups of /home, also look into rsync/grsync, very good for backups. Have a look round and find the best solution for you, have fun!

dje

---

