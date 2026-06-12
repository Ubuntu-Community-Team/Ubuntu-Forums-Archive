---
title: "how do I run program as root?"
date: 2011-07-06
forum: Desktop Environments
---

### Post by rockhoppe7 on 2011-07-06
Hi,

In 11.04 natty, I can't find a way to run a program with Administrator privileges.

Specifically,  I'm trying to configure sbackup by using the Simple Backup  Configuration frontend.  I always used to run this manually, set my  backup schedules, and then let the program carry out backups in the  background.  In the new version, the scheduling options are greyed out  unless you're logged in as Admin.

I've asked the question in the  sbackup forum (no answer so far!...) but in general terms, how do I run  an application with Administrator/root privileges?

Thanks

---

### Post by An Sanct on 2011-07-06
Open the terminal and use

```
sudo %program%
```Where "%program%" is the program you want to run.

edit: you can also press Alt+F2 and run gksudo for a GUI sudo...

---

### Post by rockhoppe7 on 2011-07-06
Thanks, I didn't know about gksudo - very useful!

---

### Post by 3Miro on 2011-07-06
sudo is for terminal applications. gksudo is for graphical ones. Using sudo for graphical applications can break parts of your system (nothing major, but some things may stop working).

If you have no more questions, please mark the thread as "solved".

---

### Post by wildmanne39 on 2011-07-06
Hi, it is best to run GUI programs  as gksu for instance if you want to open gedit with root you can type gksu gedit, the sudo command likes to make root the owner of what it opens so it is possible that it would change the ownership of the program you open too root and that is just a mess better avoided.

---

### Post by rockhoppe7 on 2011-07-07
That's great information, everyone - thanks!

---

### Post by wildmanne39 on 2011-07-07
> **rockhoppe7 said:**
> That's great information, everyone - thanks!Hi, your welcome.

---

