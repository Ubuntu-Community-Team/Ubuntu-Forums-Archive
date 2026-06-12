---
title: "C:\ Drive?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by alecjw on 2006-09-23
Where's my wine C:\ drive?

---

### Post by colo on 2006-09-23
If your wine-config's still default, it's located at ~/.wine/drive_c/

---

### Post by daou on 2006-09-23
Make sure you sure run
winecfg
before trying to access the c: drive.

Then, on a normal install, it should be located in:

~/.wine/drive_c/

---

### Post by kaisa on 2006-09-23
By default wine creates a hidden folder in your /home/ directory...

So if you wanted to change directory to the wine C drive from the terminal you would:

cd .wine/drive_c

that would then get you into the wine virtual drive.

---

### Post by alecjw on 2006-09-23
Thanks guys. I'll try it now and report back.

---

### Post by alecjw on 2006-09-23
Ok. I've found it, but it hasn't found my cd drives. Whenever i start a game which is said to work perfectley, it says that it can't find any CD drives. Anyone know how to fix this?

---

### Post by CatKiller on 2006-09-24
Run **winecfg** and click on the Drives tab. That will allow you to set up the drive letters as you wish.

---

