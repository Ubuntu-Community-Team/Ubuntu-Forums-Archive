---
title: "Document Viewer (evince) won't load/open"
date: 2011-06-30
forum: Desktop Environments
---

### Post by f-bomb on 2011-06-30
Trying to open PDFs from the web, desktop, email don't work.  I see Document Viewer start to load in the toolbar, but then it closes.  I've uninstalled and re-installed with the same result.  when I run evince from a terminal I get 

evince: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory

any suggestions?

---

### Post by wolfen69 on 2011-06-30
Completely remove evince then:
```
sudo apt-get clean && sudo apt-get autoremove
```
then reinstall.

---

### Post by f-bomb on 2011-07-11
tried that, same result after re-install:

evince: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory

---

