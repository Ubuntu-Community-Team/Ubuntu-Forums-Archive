---
title: "Manage Disk Space (find large files)"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Didjit on 2006-07-16
What is the most efficient way to manage disk space in Ubuntu. I want to be able to search for large files.

Any scripts that anyone can recommend?

TIA

Didjit

---

### Post by aysiu on 2006-07-16
Maybe something like this?

---

### Post by scxtt on 2006-07-16
you can use find:
[indent]find / -size +1G -exec ls -l {} \;[/indent]but replace 1G w/ your own size specification {i.e. 100M, 2G, 500K, etc.}

---

### Post by Didjit on 2006-07-16
> **aysiu said:**
> Maybe something like this? 
What GUI did you run? I do not get any options in the default "Search" (app-acc->Seach). My default, appears to be Beagle search.

Didjit

---

### Post by aysiu on 2006-07-16
I don't have Beagle installed (at least I don't think I do). Try Alt-F2 ```
gnome-search-tool
```

---

### Post by Didjit on 2006-07-16
> **aysiu said:**
> I don't have Beagle installed (at least I don't think I do). Try Alt-F2 ```
gnome-search-tool
```


Got it. Cool, thx. 

"Find" works too. Thanks all.

Didijt

---

