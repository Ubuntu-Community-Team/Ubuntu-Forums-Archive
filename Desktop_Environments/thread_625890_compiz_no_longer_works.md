---
title: "compiz no longer works"
date: 2007-11-28
forum: Desktop Environments
---

### Post by stuque on 2007-11-28
I have been using compiz in Gutsy Gibbon, and then due to a performance problem with Firefox I tried turning off all the screen effects. But now they won't turn back on: whenever I try to enable the effects I get a box saying it can't do it. Any ideas on how to fix this?

---

### Post by Nano Geek on 2007-11-28
Could you give us the specific error messages that you see?

---

### Post by stuque on 2007-11-28
"Desktop effects could not be enabled" appears in a box.

---

### Post by Nano Geek on 2007-11-28
Try running this in the terminal.```
compiz --replace
```

---

### Post by stuque on 2007-11-28
Aha, that seems to have worked ... I typed "compiz --replace" in the terminal and then logged out and logged back in again. Thanks!

---

