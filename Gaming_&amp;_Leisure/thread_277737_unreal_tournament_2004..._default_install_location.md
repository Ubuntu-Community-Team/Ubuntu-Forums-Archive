---
title: "unreal tournament 2004... default install location... how to get there?"
date: 2006-10-15
forum: Gaming &amp; Leisure
---

### Post by franpa on 2006-10-15
im after finding where unreal tournament 2004 was installed to and was wandering how to install the 3369 patch for it... i've got the patch but dunno where the game is loacated and dunno how to patch it...

i am a linux n00b i have only had linux for 4-5 days now... ubuntu 6.06 lts x86

-----

edit: lol after a tiny bit more searching i found where it is but now need to know the process on patching the game... do i just copy the files over?

o_O i don't have permission to right to where its installed. (i am the only user on here... how do i log in to gnome as sudo/admin?

---

### Post by NeoLithium on 2006-10-15
You bet; you just have to copy them to the directory, and allow them to overwrite the existing ones provided by the game. :)

---

### Post by franpa on 2006-10-15
how does one get access? or must i use the terminal and sudo to copy everything? (i dont have root access to there...)

---

### Post by Perfect Storm on 2006-10-15
extract the tarball file.
cd /into/the/extracted/tarball
sudo cp -r * /usr/local/games/ut2004



now just start UT2004 by;
```
ut2004
```

---

### Post by franpa on 2006-10-15
thanks very very much.... i assume cp means copy... but what is the -r command?

---

### Post by Tuna-Fish on 2006-10-15
-r means recursive, that is copy everything including subfolders

---

### Post by franpa on 2006-10-15
thanks for the info :) it works!

---

