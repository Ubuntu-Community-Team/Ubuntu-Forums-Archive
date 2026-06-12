---
title: "what happened to my disc space /sda1"
date: 2009-01-27
forum: General Help
---

### Post by alexvb on 2009-01-27
Hello, my first question on this forum.
Ubuntu 8.10 working satisfactory since about a month I noticed that my sda1 disc is getting full. Using disc usage analyzer (see attachment) I get the following non concording (in my view) information:

disc size 36.1 Gb
used space 31.8 Gb
BUT, my file system is only 10 Gb.
Where are the other 21Gb and what are they used for.
How do I free this space??

Thanks for your help in advance.

Alex van Bienen

---

### Post by marshall.robert on 2009-01-27
It's counting your other mounted drives too.

---

### Post by drs305 on 2009-01-27
If you think your disk really is getting full, here is a *how-to* on checking for undeleted Trash and other remedies if you are running out of disk space:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

For starters, you can check your disk space on mounted partitions with:
```

df -h

```

---

