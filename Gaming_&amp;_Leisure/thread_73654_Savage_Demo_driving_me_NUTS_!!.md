---
title: "Savage Demo driving me NUTS !!"
date: 2005-10-09
forum: Gaming &amp; Leisure
---

### Post by daejavu on 2005-10-09
hi .. i downloaded Savage (Online RPG) Demo ... i installed it on my Ubuntu System (Hoary)  and when doing 
                      sh savage    

im getting this as the output

 Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out




what to do ? what is going on ? how can i get this game to work !! :(

---

### Post by Perfect Storm on 2005-10-10
sudo apt-get install libtiff4

---

### Post by daejavu on 2005-10-10
it says  latesst already installed !!:(

---

### Post by Perfect Storm on 2005-10-10
Hmmm... try to run the sh file where you installed the game

cd /here/is/the/game
sh *****.sh

---

