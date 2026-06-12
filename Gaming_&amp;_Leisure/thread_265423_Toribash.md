---
title: "Toribash"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by xaque on 2006-09-25
An interesting game, sort of like slow-motion kung fu. You can control a ragdoll's limbs frame by frame, and punch and kick your opponent. 

[http://www.toribash.com/](http://www.toribash.com/)

It's Windows and Mac only, but runs under Cedega.

---

### Post by bepe86 on 2006-09-26
It's actually for Linux as well, but I haven't gotten it to run yet, all I get is

```
bepe@dell:~/toribash-linux-2.0$ ./toribash
Unable to create OpenGL screen: Couldn't find matching GLX visual
open /dev/sequencer: No such file or directory
freeglut  ERROR:  Function <glutSolidSphere> called without first calling 'glutInit'.
```

Anyone has any idea what that means? I have SDL, SDL-mixer and freeglut installed.

---

### Post by louman on 2006-10-02
i have the exact same problem; has anyone gotten it to work at all?

---

### Post by Perfect Storm on 2006-10-03
Works fine here.

Execute ./toribash_ubuntu

---

### Post by sixblades on 2007-09-23
I've just got it to work here (although not very quickly). I just kept doing repeated "ldd toribash_ubuntu7" and searching for the missing libraries until all were accounted for, and it ran fine.

---

### Post by Cappy on 2007-09-23
You could use getlibs ( [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ) and run it on it instead:
```
sudo getlibs toribash_ubuntu7
```
Of course you will need to be in the directory of the extracted program when you do that.

---

### Post by sixblades on 2007-09-23
Hey, there's a nifty shortcut... :D

---

