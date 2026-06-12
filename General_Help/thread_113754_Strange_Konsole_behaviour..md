---
title: "Strange Konsole behaviour."
date: 2006-01-07
forum: General Help
---

### Post by z-vet on 2006-01-07
Hi all.
When i type or paste long lines in Konsole, it doesn't wrap a line and jumps to a new line to continue, but stays in the same line and continues from line's beginning, erasing what i typed before. :confused: 
Just look at attached image to see what i mean: i pasted an amaroK 'configure' command in there and what you see under the cursor was my prompt. 
[[IMG]http://img352.imageshack.us/img352/5592/hex22te.th.png[/IMG]](http://img352.imageshack.us/my.php?image=hex22te.png)
I have no such behaviour in terminal, only with graphical tools like Konsole or Yakuake. Please help, it driving me nuts. :mad:

---

### Post by z-vet on 2006-01-07
Checked now and found that it happens with any terminal, not only graphical ones... :(

---

### Post by salil on 2007-07-17
I experienced the same problem a while ago. What I happened to notice was that you too had a colored prompt. I removed the color directives from the PS1 environment variable and now it works fine. I added
```
export PS1='\u@\h \W\$ '
``` to my .bashrc (in fact, you can customize the prompt in whatever way you want by modifying the environment variable PS1. For more info, use google)
Now the line wrapping works fine.

Although this thread is quite old, I thought I'll post my fix anyway, in case someone out there is facing the same problem.

-Salil.

---

