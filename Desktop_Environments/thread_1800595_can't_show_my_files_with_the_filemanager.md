---
title: "can't show my files with the filemanager"
date: 2011-07-09
forum: Desktop Environments
---

### Post by Mappenz on 2011-07-09
Hi,

i get this message when i try to open my folder with the filemanager supplied by xubuntu.

```
Fehler beim Untersuchen der Datei /home/michael/.gvfs mit fstat(): Der Socket ist nicht verbunden.
```A quick google search didn't bring results. What does this mean and how to fix it?

---

### Post by Toz on 2011-07-09
Are you using gigolo? I was getting the same error message after I suspended/resumed when using gigolo.

```
fusermount -u ~/.gvfs
```would unmount all of my shares and get me access to my home directory again.

---

### Post by Mappenz on 2011-07-09
WORKS, thx.

I'm not using gigolo though. I also don't suspend, since the backlight would turn of and never come back on again on my travelmate 7735z : ).

---

