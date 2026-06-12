---
title: "What's the &quot;empty trash&quot; command?"
date: 2010-11-11
forum: Desktop Environments
---

### Post by damnated on 2010-11-11
Basically I want the same thing this guy did [http://wwww.ubuntuforums.org/showthread.php?t=89638](http://wwww.ubuntuforums.org/showthread.php?t=89638) . 
Mind you, the trash isn't under ~/.Trash anymore, and I have no idea where it is TBH. So basically I need the location of the Trash in lucid, I presume the actual emptying command will work.

---

### Post by sisco311 on 2010-11-11
It's ~/.local/share/Trash/

So you have to run:
```
rm -rf ~/.local/share/Trash/*
```

---

### Post by damnated on 2010-11-11
That's not it, for one running the script on a non-empty trash doesn't do anything, and second, opening that folder confirms that it is empty, no hidden files either.

---

### Post by sisco311 on 2010-11-11
Well, if the deleted files were on another partition then the trash should be under path/to/partition/.Trash or path/to/partition/.Trash-**$uid** (where $uid is the user id of the user who deleted the files). See:  [http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

Anyway, if you install the trash-cli package, you can empty the trash with:
```
empty-trash
```

---

### Post by damnated on 2010-11-11
I have only one partition on my file system and I have files in the trash that were originally on said file system. Yet the folder ```
~/.local/share/Trash 
``` is empty.

EDIT: Ha, it did empty the trash, but the icon didn't change to the "empty bin" icon. Kinda weird. Also ```
empty-trash
``` empties the trash as well, but for some reason the icon still wont update, what's even worse is if I hover over it, it says "8 items in Trash". It doesn't change even if I right click on it, and "empty trash"....

---

### Post by mister_playboy on 2010-11-12
> **damnated said:**
> empties the trash as well, but for some reason the icon still wont update, what's even worse is if I hover over it, it says "8 items in Trash". It doesn't change even if I right click on it, and "empty trash"....

I remember this behavior from the 8.10 days.  My workaround was to delete the trash icon from the panel and re-add it when it got "stuck". :)

---

