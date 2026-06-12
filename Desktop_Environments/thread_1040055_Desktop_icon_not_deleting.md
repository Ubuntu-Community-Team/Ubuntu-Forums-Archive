---
title: "Desktop icon not deleting"
date: 2009-01-15
forum: Desktop Environments
---

### Post by Schok on 2009-01-15
I have a .zip file on my desktop and i can't seem to delete it. Everytime i delete it(move to trash) it says "Error trashing file: no such file or directory" but the icon is still on the desktop. Is there a way to get rid of it?

8.10 x64 Aspire 5050 AMD Turion 64 Mobile Technology MK-38 ATI RADEON X1100 2GB RAM and dual booted with xp

---

### Post by cdtech on 2009-01-15
open a terminal and look within the ~/Desktop directory if you see the file use the "rm filename" command to rid it.

---

### Post by ajcham on 2009-01-15
If you navigate to the desktop directory in nautilus, are you able to delete from there? (~/Desktop)

Alternatively:
```
rm ~/Desktop/filename.zip
```

---

### Post by adamlau on 2009-01-15
Reboot your computer after following the steps above.

---

### Post by Schok on 2009-01-18
i couldn't delete it using any of the methods above but a restart solved it..weird..

---

