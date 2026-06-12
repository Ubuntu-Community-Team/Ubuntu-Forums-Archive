---
title: "Problem with apt-get"
date: 2006-08-21
forum: Desktop Environments
---

### Post by flugheim on 2006-08-21
Hi, i got this error when i tried to install the .deb package for jEdit:
> E: the packeage jedit needs to be reinstalled, but i cant find an archive for it.
E: Internal error opening cache (1). Please report.

And i dont manage to remove it, so i wonder if anyone could help me a bit?

---

### Post by peabody on 2006-08-21
> **flugheim said:**
> Hi, i got this error when i tried to install the .deb package for jEdit:


And i dont manage to remove it, so i wonder if anyone could help me a bit?

I take it you're using dpkg with a .deb file instead of apt-get correct?  How exactly did you try to install jEdit?

---

### Post by flugheim on 2006-08-21
I just doubleclicked it, and installed it.. And after i did that no packaging tools worked..

---

### Post by peabody on 2006-08-21
> **flugheim said:**
> I just doubleclicked it, and installed it.. And after i did that no packaging tools worked..

sudo dpkg -r jedit

then try apt again.

---

### Post by flugheim on 2006-08-21
> **peabody said:**
> sudo dpkg -r jedit

then try apt again.
Im sorry for the bad translation

flugheim@laptop:~$ sudo dpkg -r jedit
Password:
dpkg: Error when treating jedit (--remove):
 The package is in a very bad conditiion. You should
reinstall the package befor you try to to remove it.
It occoured an error while treating:
 jedit


But it doesent help to reinstall it..

---

### Post by LKRaider on 2006-08-21
Where did you get the package from? Seems someone made a bad work on packaging that program.

Anyways, to be able to finally remove it, try this:

```
sudo dpkg --remove --force-remove-reinstreq jedit
sudo dpkg --purge jedit
```

And don't install that same package again!

---

### Post by flugheim on 2006-08-25
Thanks LKRaider, the first one solved it :)

---

