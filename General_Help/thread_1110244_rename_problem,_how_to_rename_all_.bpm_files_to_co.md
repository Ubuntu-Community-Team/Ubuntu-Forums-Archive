---
title: "rename problem, how to rename all *.bpm files to cover.bmp"
date: 2009-03-29
forum: General Help
---

### Post by nlz on 2009-03-29
I need to convert all *.bmp files to cover.bmp on my Ipod (so rockbox can read and show my album art). I really don't understand the PERL arguments for rename. Can someone help please?

---

### Post by nlz on 2009-03-30
rename doesn't work recursively so please use this command (thanks to ferret @ #perl )

```
 find . -name '*.bmp' -execdir mv {} cover.bmp \;

```

---

