---
title: "Compiz lag"
date: 2009-08-09
forum: Desktop Environments
---

### Post by Paperfairy on 2009-08-09
I have installed Compiz in order to enable Desktop effects - but now when I enable them using the preferences, my computer slows down terribly, and I lose my window's title bars. Turning the effects off or metacity --replace cures the problem.

In the past, I was able to use all Desktop effects without any problems or noticeable lag... so why now?

[http://ubuntuforums.org/showthread.php?t=1229839](http://ubuntuforums.org/showthread.php?t=1229839) <- my previous Compiz problem, may provide insight to situation

---

### Post by gjoellee on 2009-08-09
Why turning Metacity on and Compiz off helps, is because both are window mangers. Only one of them can run at the same time.

What is the output of ```
lspci | grep VGA
```

---

### Post by Paperfairy on 2009-08-09
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Intergrated Graphics Controller (rev 0c)

---

### Post by gjoellee on 2009-08-10
You can try to go to System->Administration->Drivers (or something similar)
then see if ant drivers appear. If not there are some drivers here: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)


If you get further issues with Compiz this might help you:
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

### Post by Arup on 2009-08-10
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Paperfairy on 2009-08-16
Yeah, none of that worked. Anyways, a reinstall of compiz fixed everything.

---

### Post by gjoellee on 2009-08-16
> **Paperfairy said:**
> Yeah, none of that worked. Anyways, a reinstall of compiz fixed everything.

Haha! :lolflag:

---

