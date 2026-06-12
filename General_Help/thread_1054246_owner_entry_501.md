---
title: "owner entry 501"
date: 2009-01-29
forum: General Help
---

### Post by kennydidit on 2009-01-29
hey all I have several folders that end up having an owner entry of 501 I found this [thread]("http://ubuntuforums.org/showthread.php?t=936350&highlight=owner+501") and I used the command (sudo nautilus) which I changed the folder  ownership to match everything else on my PC, but the files in side those folders still are lock and owner is still 501. Is there a way I can change all the files in a folder at once? (most of these files are pic's and I have hundreds) I tried hitting the button on the bottom  that says Apply permission to enclosed files, but nothing happens.

---

### Post by dcstar on 2009-01-29
> **kennydidit said:**
> hey all I have several folders that end up having an owner entry of 501 I found this [thread]("http://ubuntuforums.org/showthread.php?t=936350&highlight=owner+501") and I used the command (sudo nautilus) which I changed the folder  ownership to match everything else on my PC, but the files in side those folders still are lock and owner is still 501. Is there a way I can change all the files in a folder at once? (most of these files are pic's and I have hundreds) I tried hitting the button on the bottom  that says Apply permission to enclosed files, but nothing happens.

```
man chown
man chmod
```

---

