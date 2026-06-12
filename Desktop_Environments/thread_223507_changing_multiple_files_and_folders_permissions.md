---
title: "changing multiple files and folders permissions?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by ELD on 2006-07-26
Hi all i need to change a folder and all files and folders inside's permissions, how can i do this?

---

### Post by Dubbayoo on 2006-07-26
maybe something like:

find . -type d -print | xargs chmod 755
or 
find . -name "*.mp3" -print | xargs chmod 664

---

### Post by aysiu on 2006-07-26
```
chmod -R 755 /folder/name
``` Or you could just right-click it and select **Properties**... if you're using KDE.

---

### Post by ELD on 2006-07-27
i take it -r means recursive or something so it does all inside?

---

### Post by aysiu on 2006-07-27
Yes, **-R** means it's recursive.

It's a capital **-R**, though--not a lowercase **-r**.

---

