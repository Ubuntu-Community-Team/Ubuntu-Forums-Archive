---
title: "&quot;Funny&quot; bug: cut but not copy..."
date: 2009-02-20
forum: General Help
---

### Post by JulienEP6 on 2009-02-20
Hallo to you all: here is my problem...

background of the problem: I am using ubuntu 8.04 and trying to organize a bit my files, in the windows server of my group which I access using Samba... 

And so here is what happened:
If I want to move a folder no problem, everything is working fine...
But if I want to copy/paste it.. some file do not work... I have a "permission denied" after copying a few files... And if I do it via the terminal it does just say me: "cp: omitting directory [*pathway of the directory*]".. Any idea?

... Sorry for maybe not giving quite helpful indications, I'm a bit newbie :p

---

### Post by heindsight on 2009-02-20
If you want to copy an entire directory use:
```
cp -R source dest
```

have a look at the manual
```
man cp
```

---

### Post by JulienEP6 on 2009-02-25
Waa so simple ^^... Thanks a lot!:KS

---

