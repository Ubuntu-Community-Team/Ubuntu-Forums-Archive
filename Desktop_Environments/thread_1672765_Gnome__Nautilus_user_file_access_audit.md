---
title: "Gnome / Nautilus user file access audit"
date: 2011-01-21
forum: Desktop Environments
---

### Post by RRJ on 2011-01-21
Hello,

I am wondering if some1 able to help me.
i need to track every single users file access attempt (read file, delete file, move file etc).
Does Gnome or Nautilus provide such function? or maybe there is some software that provides this functionality?
auditd is not what i want, as any file access attempt  is being loged as exe=nautilus so i cant make any difference between actions users is taking. 

Help any1?

---

### Post by littleemperor on 2012-01-11
Noobie looking for the same thing, if anyone has suggestions, it would be great in simple terms. 

thanks

---

### Post by Kslawdog on 2012-01-11
You can try the "m" command, for example

```
m -(option) username
```

type man m in terminal to find out more

---

