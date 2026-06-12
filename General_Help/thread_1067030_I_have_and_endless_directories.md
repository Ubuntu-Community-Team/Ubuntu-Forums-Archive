---
title: "I have and endless directories"
date: 2009-02-11
forum: General Help
---

### Post by Dr Zin on 2009-02-11
I have this directory that is go on and on its taking up over 50 GB of space.

so I tried doing the trash  thing but that is taking for ever. 

and i have done this before but i can't remember how

```
rm -r /home/drzin/Desktop/drzin 
```

---

### Post by Dr Zin on 2009-02-11
```
Desktop$ rm -r -f /home/drzin/Desktop/drzin

```

---

### Post by kanikilu on 2009-02-11
The command you have there will work, but I think it will ask you to confirm deleting every file. You can use the force option in addition to recursive (-rf) to keep if from asking you to confirm. 

**DISCLAIMER**: Only do this if you are *sure* you want everything under that directory permanently removed, and only after double-checking your path to make sure you don't accidentally delete something else. Used wrong, that command can hose your system!

/EDIT - nevermind, you got it.

---

### Post by Dr Zin on 2009-02-14
Cool thanks

---

