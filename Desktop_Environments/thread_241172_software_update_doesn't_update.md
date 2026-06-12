---
title: "software update doesn't update"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Presuntu on 2006-08-21
I have 3 update ready to be installed. I click on install, Ubuntu checks the system, then nothing. I click again, it re-checks the system (building tree dependency) then nothing, and so on.

Why doesn't install them? Any known bug?

---

### Post by hopstah on 2006-08-22
i have been having that same problem, and i don't know how to fix it, but i do know how to install that stuff anyway.

open up a terminal and enter the following
```
sudo aptitude update
sudo aptitude upgrade
```
and that will install all of the updates that you have pending.  if someone else knows how to fix the graphical installer, i would love to know as well.

---

### Post by Presuntu on 2006-08-22
thanks man, that would fix it for now, but I definitively want the software update back!

---

### Post by hopstah on 2006-08-22
the end result is exactly the same, and personally i enjoy working in the console, but i understand that not everyone does.

---

### Post by Presuntu on 2006-08-23
How is it possible that just two people have this problem?

Nobody else have problems with the system update?!

Please, help!

---

### Post by hopstah on 2006-08-23
i don't know if you have fixed this yet, but i found this fix in another thread about this same problem
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

---

### Post by Presuntu on 2006-08-23
Thank you!!! Yes, that solved the annoing problem!

Thanks!

-Presi

---

