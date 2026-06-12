---
title: "[SOLVED] CLI apps stay open after I Ctrl-Z to exit"
date: 2006-09-24
forum: Desktop Environments
---

### Post by icheyne on 2006-09-24
If I run a CLI application and then click ctrl-Z to exit, it stays open in my process list. How can I shut a program down from the command line before I exit?

---

### Post by Ramses de Norre on 2006-09-24
Does it happen with all programs or just one particular? 
If I test it out with top here it works..

---

### Post by ayoli on 2006-09-24
CTRL + z send app in the background, so it's still running, you can retrieve it by type in:
```
fg app_name
```
if you want to exit a CLI app hit CTRL + c

---

### Post by icheyne on 2006-09-24
> **ayoli said:**
> CTRL + z send app in the background, so it's still running, you can retrieve it by type in:
```
fg app_name
```if you want to exit a CLI app hit CTRL + c

That explains it. Thanks!

---

