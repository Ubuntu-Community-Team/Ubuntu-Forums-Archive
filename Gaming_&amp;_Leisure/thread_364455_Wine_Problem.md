---
title: "Wine Problem"
date: 2007-02-18
forum: Gaming &amp; Leisure
---

### Post by Hickeydog on 2007-02-18
I'm having a wine problem.  I installed wine and ran winecfg, but when I go to open a .exe, I get the error message:
Cannot open /media/cdrom0/SETUP/ENGLISH/SETUP.EXE: No application suitable for automatic installation is available for handling this kind of file.

and when right click and go under"Open with other application" wine is not there.  Did I miss something in the install?

---

### Post by highneko on 2007-02-18
From a terminal what happens when you type:
wine "/media/cdrom0/SETUP/ENGLISH/SETUP.EXE"

---

### Post by Hickeydog on 2007-02-18
I was denied
bash: /media/cdrom0/setup/english/setup.exe: Permission denied
and then I realize that  i failed to type the wine part of it, and once I did that, it worked.  
Do you know how I can wine to automatically open .exe files

---

### Post by meng on 2007-02-18
Linux is case-sensitive - did you enter the filename accurately?

---

### Post by Hickeydog on 2007-02-18
yeah.  I got it to work once I added the wine part to it

---

