---
title: "No rights to unzip to folder"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Calleponken on 2006-09-02
Hi, I hope this is the right place to ask this question.

I have downloaded a skin for amsn, and i was instructed to unzip it in /usr/share/amsn/skins

When I try to do so it says that I haven't got the rights to do it.

What should I do? I'm a complete newbie as I installed Ubuntu this very morning.

Cheers Carl

---

### Post by ayoli on 2006-09-02
you need root rights to write in /usr subfolders, so in a terminal type in:
```
sudo unzip /path/to/yourzip -d /usr/share/amsn/skins
```

---

### Post by Calleponken on 2006-09-03
Thanks! Now it works perfectly. I'm new to this terminal thing and I'm trying to learn as fast as possible! 

A moderator may lock this thread if that is what you do.

---

