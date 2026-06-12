---
title: "Can't Boot into GUI"
date: 2009-03-03
forum: General Help
---

### Post by abyrne on 2009-03-03
Hi,

  I just installed Ubuntu on my ext. HD as a take-it-anywhere operating system. I plugged it into my school's widescreen acer PC to fix some Windows crap. I tried to plug it back into my home laptop (Toshiba Satellite). I got to GRUB and selected boot normally, then it just booted into a command line. I tried recovery mode, no luck. I'm  trying to convince my headmaster into converting the school's PCs from Windows to Ubuntu, and its not too convincing if Ubuntu won't even boot into the GUI. Thanks :KS

---

### Post by abyrne on 2009-03-04
Bump

---

### Post by theozzlives on 2009-03-04
have you tried startx?

---

### Post by abyrne on 2009-03-04
Is startx a command?

---

### Post by abyrne on 2009-03-04
Tried startx, but all I got was an error message that was like
```
Fatal error
no screens found
Giving up
```

I think this has something to do with my display card. When I plugged it into my school's computer, Ubuntu had to run in low graphics mode. Now there is no graphics at all on my PC. 
HELP:(

---

### Post by konqueror7 on 2009-03-04
yup, just login in the command line, and type,
```
startx
```

---

### Post by konqueror7 on 2009-03-04
try,
```

sudo /etc/init.d/gdm start
startx
```

---

### Post by abyrne on 2009-03-04
Thanks for the help,

 but none of ur commands worked. I just ran xfix from the recovery console and it worked
THx anyway though!:D

---

