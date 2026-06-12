---
title: "Wine doesn't see all folders under program files..."
date: 2007-12-09
forum: Desktop Environments
---

### Post by betapaul on 2007-12-09
When I attempt to configure Wine it only shows "common files" and " internet explorer" under the program files folder on the C drive.  There should be many applications under there as I'm dual booting.  I'm a noob.  Ideas?

---

### Post by lswest on 2007-12-09
WINE's C Drive isnt your actual windows drive, it's just a folder where the installed programs go, if you want other programs installed, you have to install them by running the installs (.exe, .msi, etc.) files in wine, and then allowing the install to run through

---

### Post by betapaul on 2007-12-09
Gotcha!  That makes sense...so in order to run iTunes through Wine, I would download the .exe file and place it where?

---

### Post by Bölvaður on 2007-12-09
1. Download the program_name.exe onto your desktop           // note that program_name should be replaced by the program you wish to 
2. Open it with WINE, by terminal (or right clicking with mouse and choose open with wine).
in terminal it should be:
```
cd Desktop
wine program_name.exe
```

What I like to do when there are long names like "program_name.exe". Is to type the first 2-3 letters and then press Tab, Then it automatically types the last part of the word if no other file or folder has same beginning.

---

