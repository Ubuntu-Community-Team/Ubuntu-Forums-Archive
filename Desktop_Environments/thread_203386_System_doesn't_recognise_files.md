---
title: "System doesn't recognise files"
date: 2006-06-25
forum: Desktop Environments
---

### Post by tomcio on 2006-06-25
Hi!

I have strange problem. Suddenly after reboot GNOME doesn't recognise many files's types. For example it doesn't know now how to open ZIP, RAR, BZIP2 tec. archives, pictures, OpenOffice documents, generally it doesn't know how to open any file and it "see" all files beside text files as "program".

How to fix it?! Maybe it seems to be a small problem, but it make whole system unable to work!

Help me! :sad:

---

### Post by ayoli on 2006-06-25
Try to run the following commands as root in a terminal:
```
$ /usr/bin/update-mime-database /usr/share/mime
$ /usr/bin/update-desktop-database
```
should do the job.
regards

---

### Post by tomcio on 2006-06-25
Great! THX!

I works, but I wonder if you can explain me what cloud be a reason of this... bug? It' can be good to now that, before I'll do it next time ;)

---

### Post by ayoli on 2006-06-25
your mime database was messed up maybe due to an update or a system crash

---

