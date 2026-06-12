---
title: "Firefox Won't Start"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Doovoo on 2006-07-02
So, all of the sudden, firefox won't start. When I try to start it, it will just give me the bar in the panel with the "starting firefox" and then that will just disappear and give me nothing. I've tried reinstalling and killall and rebooting but nothing has worked. 

Help?

---

### Post by Doovoo on 2006-07-02
Alright, when I try starting it from the terminal, I get

```
Floating Point Exception
```

What does that mean, and how do I cure it? Any help is appreciated.

---

### Post by user1397 on 2006-07-02
[quote=Doovoo]Alright, when I try starting it from the terminal, I get

```
Floating Point Exception
``` 
What does that mean, and how do I cure it? Any help is appreciated.[/quote]try this:  open a terminal and type ```
 ls -l .mozilla/firefox/*.default/lock
``` If you see a file there, delete it and then re-launch firefox

---

### Post by Doovoo on 2006-07-02
Okay, I fixed the problem.

I found [this]("http://ubuntuforums.org/showthread.php?t=190474&highlight=floating+point+exception") thread, and realized I had just installed fonts right before having this problem. So I just deleted the fonts I tried to install.

This is a really problematic bug, the fact that Firefox won't play well with new fonts. As a graphics student, this discourages me.

---

