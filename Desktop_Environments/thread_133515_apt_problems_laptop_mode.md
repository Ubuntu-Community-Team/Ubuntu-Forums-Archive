---
title: "apt problems laptop mode"
date: 2006-02-20
forum: Desktop Environments
---

### Post by chubsmalone on 2006-02-20
I'm running breezy on a dell inspiron 1200.  I tried to install laptop mode tools with apt and it hangs with no response.  I can't remove it because apt says that it isn't installed...same with dpkg --remove.  Is there a way to cancel that install and try it again?

---

### Post by jml75 on 2006-02-20
Are you able to install other packages with apt-get?

Or does your internet connection work on that computer?

---

### Post by Ramses de Norre on 2006-02-20
You can always cancel it with ctrl+c

---

### Post by chubsmalone on 2006-02-21
I did cancel it with ctrl + c.  Afterwards, I try to do an apt-get upgrade and it tells me:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

I do 'dpkg --configure -a' and it hangs again at the same place.  

What I want to do is remove the offending package from the queue, so to speak so I'm not getting the error every time I use apt.

---

