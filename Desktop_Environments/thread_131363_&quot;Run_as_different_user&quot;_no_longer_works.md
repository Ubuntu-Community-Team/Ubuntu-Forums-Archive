---
title: "&quot;Run as different user&quot; no longer works"
date: 2006-02-16
forum: Desktop Environments
---

### Post by jphantom on 2006-02-16
SystemTools->Run as different user was working last night but no longer works.  

When I click on it the mouse does it's thinking animation for a while and then nothing happens.   I cannot find any corresponding error in the log files.

---

### Post by taurus on 2006-02-16
One place is in ~/.xsession-errors...

---

### Post by jphantom on 2006-02-16
I believe I narrowed it down to either: 

1) bad icon set
2) improper startup after suspend

---

