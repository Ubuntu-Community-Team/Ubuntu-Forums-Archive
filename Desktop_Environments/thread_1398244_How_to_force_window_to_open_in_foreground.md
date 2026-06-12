---
title: "How to force window to open in foreground?"
date: 2010-02-04
forum: Desktop Environments
---

### Post by jazzgossen on 2010-02-04
Is there a way in Ubuntu, running Compiz or Metacity, to force a program to open in the foreground? 

My specific scenario is that I have a PDF presentation running full-screen and I also have a shell script that starts a full-screen mplayer session, playing an animation. However, when the script runs, the video plays behind the PDF presentation (shown in Impressive), so that it's invisible.

Is there a command-line way to force it to the foreground?

---

### Post by zlatkart on 2010-02-04
```
wmctrl -a :ACTIVE:
```       
should work (if wmctrl installed

---

### Post by rewyllys on 2011-09-18
> **zlatkart said:**
> ```
wmctrl -a :ACTIVE:
```       
should work (if wmctrl installed
Thanks, Zlatkart.  Your code cured my problem!:popcorn:

---

