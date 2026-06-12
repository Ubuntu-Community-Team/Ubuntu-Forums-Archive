---
title: "problem in places on toolbar"
date: 2011-02-20
forum: Desktop Environments
---

### Post by gazoboy on 2011-02-20
in toolbar i have 3 options ie places /apps etc.. using places i have home folder / music/pictures docs vidios etc.. when i use movie player/or ryambic box...once  i cannot open any progam without movie player opening by default... ie i click on pictures and movie player trys to open,,  have reinstalled twice so thats no answer,,,gaz

---

### Post by gazoboy on 2011-02-20
i get a problem using the home folder (accessed from menu bar under places.. once i have used movie player any file i open in home folder 9ie docs or pictures gets opened by movie player even though it doesnt play pictures,,,i have already reinstalled ubuntu 10.10 and have tried the gnome media player with the same results'''gaz

---

### Post by Krytarik on 2011-02-20
Hi and welcome to the forums,

you may have inadvertedly chosen those media players as default app to handle folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by Krytarik on 2011-02-20
Duplicate thread of this one:
[http://ubuntuforums.org/showthread.php?t=1691897](http://ubuntuforums.org/showthread.php?t=1691897)

I did answer there.

---

### Post by Bucky Ball on 2011-02-20
Welcome.

A note: Duplicate threads are against forum rules and make life very confusing. I have asked mods to merge your threads. ;)

---

### Post by cariboo on 2011-02-21
Please don't create multiple threads on the same subject. I have merged your two threads

---

