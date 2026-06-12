---
title: "wine"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by atlfalcons866 on 2007-01-12
hi

How do i start wine? i already downloaded? do i just start the ,exe?

---

### Post by Sqwishy on 2007-01-12
run winecfg in console and set it up ... then either left clicky on the exe or right click and make sure it opens in wine. or run in terminal ' wine <PathOfFile> '

---

### Post by Enverex on 2007-01-12
Best ways of doing it are either chdir'ing to the folder where the EXE is then doing 'wine appname.exe' or if it's located somewhere inside your "virtual drives" then doing 'wine "C:\Games\Tron\Tron.exe"' or whereever it's located. Running things directly from Nautilus/Konqueror or running them line 'wine /home/bob/stuff/app.exe' aren't supported because they don't always work.

If you want a GUI then you can do 'wine explorer' which will give you a browser and you can run things from there which may be easier for you.

---

