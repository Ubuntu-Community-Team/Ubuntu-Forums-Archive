---
title: "QFile::writeBlock: File not open"
date: 2006-06-21
forum: Desktop Environments
---

### Post by shizow on 2006-06-21
since i upgraded to dapper
i get sometimes a lot of errors when i start an application like gimp or some other apps
saying just
"QFile::writeBlock: File not open"
like 100 times in a row
but then start the app normally

any suggestions?

---

### Post by shizow on 2006-07-08
any help, please?

---

### Post by shizow on 2006-07-28
please!!

---

### Post by Mike Orr on 2007-05-07
Thanks to your post and a Google search and strace, I figured this out.  I have it happening with gvim.  The culprit was a file ~/.gtk_qt_engine_start owned by root:root, so the program did not have write permission to it.  "chown ME:ME ~/.gtk_qt_engine" eliminated the annoying message.

---

