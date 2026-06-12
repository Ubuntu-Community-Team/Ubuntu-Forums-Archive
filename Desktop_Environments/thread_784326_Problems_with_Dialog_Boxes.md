---
title: "Problems with Dialog Boxes"
date: 2008-05-06
forum: Desktop Environments
---

### Post by ardoaamch on 2008-05-06
When I am using a program and try to open a dialog box such as "Save As..." in Firefox or gEdit, the program will hang for about 20 seconds before the box will pop up.  The system will work fine, and I can do other things, it is just that program that freezes.  It just started happening.  Everything was working fine before.  Any ideas as to why this is happening?

---

### Post by KungFuGeek on 2008-05-06
I am having the exact problem

If i click save as in ANY program the program freezes for about 20-30 seconds before the dialog opens up. This also happens when i click open file in any program.


I'm running 8.04, and the only changes i have made from the default is to downgrade to firefox 2

---

### Post by KungFuGeek on 2008-05-12
anybody have any ideas?

---

### Post by mike.geeves on 2008-05-21
Hey,
Same problem here and after much head scratching it seemed to be related to the 'Tracker' indexer (here at least...)
Quick fix for me was to just login as another user or CLI and rename (or delete..) the .cache dir in my home and log back in again

The indexer applet (magnifying glass one) then came back as well... I suppose you should probably move some files out of your home dir and re-index if you use using it, I think I'll probably just uninstall it though

FYI, files in my .cache/tracker dir looked like:
~$ ls -ltrh cache-problem/tracker/
total 378M
-rw------- 1 lith lith  12K 2008-02-04 17:37 email-contents.db
-rw------- 1 lith lith  96K 2008-02-04 17:38 email-meta.db
-rw------- 1 lith lith 2.5M 2008-05-07 09:40 file-update-index.db
-rw------- 1 lith lith 1.2M 2008-05-07 09:40 email-index.db
-rw------- 1 lith lith  80M 2008-05-07 11:52 file-contents.db
-rw------- 1 lith lith 105M 2008-05-07 11:52 file-index.db
-rw------- 1 lith lith  17K 2008-05-07 14:22 file-meta.db-journal
-rw------- 1 lith lith 190M 2008-05-21 11:43 file-meta.db

Quite large...guessing it's the time to scan through them that causes the delay...not sure why it's doing that when you're trying to save though! :)

---

### Post by ardoaamch on 2008-05-21
Thank you very much!  Your suggestion worked perfectly.  I wonder what it is that makes this happen?

---

### Post by mody on 2008-08-18
Been hit by the same problem. Solved by restarting trackerd daemon.

HTH
Mody

---

### Post by Karl_jv on 2008-08-19
Removing the cache didn't work instantly for me. But when I manually started tracker-applet my computer suddenly sprung to life again.

Thanks for the help!

---

