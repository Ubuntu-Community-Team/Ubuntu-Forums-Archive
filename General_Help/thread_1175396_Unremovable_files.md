---
title: "Unremovable files"
date: 2009-06-01
forum: General Help
---

### Post by quinnten83 on 2009-06-01
Hi all, 
I am trying to remove a folder on my external harddrive.
This file is from a backup I once did.
Now everytime i try to remove it, i get an error

```
Me@Desktop:/media/Extbackup/20081026 Backup Compaq laptop/Windows/C drive/Program Files/Real/RealPlayer/DataCache/Login/data$ ls -al
ls: cannot access buttons.js: Input/output error
ls: cannot access countries.js: Input/output error
ls: cannot access form_elements.js: Input/output error
total 0
drwxrwxrwx 1 root root 0 2008-10-26 15:06 .
drwxrwxrwx 1 root root 0 2009-01-17 18:07 ..
-????????? ? ?    ?    ?                ? buttons.js
-????????? ? ?    ?    ?                ? countries.js
-????????? ? ?    ?    ?                ? form_elements.js

```

no matter what I try I can't get rid of it. 
I've tried doing it in windows, and in Linux nothing.
DO you guys have any ideas how I can remove this?

---

### Post by mike555 on 2009-06-01
You could install and try "nautilus gksu" in Ubuntu , just right click on the folder and click "open as administrator" , then delete it .....

---

### Post by quinnten83 on 2009-06-02
I have egg on my face, and I would go all red if you could see it.
I just ran nautilus as root and it deleted like nothing....
Why didn't I think of that before???

Tnx
Mike555

---

### Post by ronny_abraham on 2009-07-22
This was incredibly helpful.  But how does nautilus do that? I mean, I'd like to be able to do that from the command line.

---

