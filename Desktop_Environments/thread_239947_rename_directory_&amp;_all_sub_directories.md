---
title: "rename directory &amp; all sub directories?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by soliac on 2006-08-20
Hi, I have got a folder where all subdirectories in it have got "(2)" at the end of their name. How can I batch rename all subdirectories within this folder to remove that "(2)" ??? I don't know how to use regular expressions, could someone help?

---

### Post by IYY on 2006-08-20
```
for x in *"(2)"*
do 
mv "$x" "`echo $x | sed "s/(2)//g"`"
done

```

This will work for most cases, but will remove (2)'s from the middle of the filename as well as end, and will not work if a directory of the same name already exists.

---

### Post by soliac on 2006-08-20
Thankyou! This has done it, except there are still some sub sub-directories unchanged. Could I batch rename those too or do I need to do it manually?

---

