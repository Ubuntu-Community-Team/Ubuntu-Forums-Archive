---
title: "Can't copy CD"
date: 2008-12-14
forum: General Help
---

### Post by Stoodle on 2008-12-14
Whenever I try to copy a CD, the CD drive immediately unmounts. Also, I can't eject CDs. The button doesn't work on the computer, eject in terminal doesn't work, and there's nothing in the GUI to allow me to eject. It'll just eject randomly when it's supposed to be copying. Otherwise, I have to press the small button with a paperclip.

---

### Post by geirha on 2008-12-14
My first guess would be that the cd drive is broken. Do you have any other OSes to test it with?

The kernel logs should hopefully give some indication of what's wrong. Run the command **dmesg** in a terminal and post the output.

---

### Post by Stoodle on 2008-12-14
Dmesg has too long of an output so the terminal won't hold it. I don't know Linux as much as I should, so I don't know where the log is actually kept. The button works when it wants. I have Windows but it's unusable right now.

---

### Post by geirha on 2008-12-14
```
dmesg > /tmp/dmesg.txt
``` will store the output of dmesg to the file /tmp/dmesg.txt.

---

### Post by Stoodle on 2008-12-14
It's all just Internet traffic it seems.

---

### Post by exploder on 2008-12-14
If you are running Ubuntu 8.10 there is a udev update that should be of help as long as your drive is in working order. There is also a newer version of Brasero here.

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

The new version addresses some serious bugs that were in the previous version.

---

### Post by Stoodle on 2008-12-15
Both apparently newest version.

---

### Post by spcwingo on 2008-12-15
Is the drive a Mitsumi?  If so, there's already been a bug reported on it.  I also have a Mitsumi CD/RW drive with the same problems.  I just plan on finding a used non-Mitsumi CD/RW drive on fleabay.

---

