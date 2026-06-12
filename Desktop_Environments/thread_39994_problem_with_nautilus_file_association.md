---
title: "problem with nautilus file association"
date: 2005-06-07
forum: Desktop Environments
---

### Post by hysun on 2005-06-07
hi, i am using ubuntu 5.04. previously installed on my computer, works fine. then i re-installed it (due to some reasons), and now when i try to add an associated application to a file type (by "file".property --> Open With --> Add), i get an error saying:

Could not add application
Could not add application to the application database

anyone can help me out? thanks

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=hysun]hi, i am using ubuntu 5.04. previously installed on my computer, works fine. then i re-installed it (due to some reasons), and now when i try to add an associated application to a file type (by "file".property --> Open With --> Add), i get an error saying:

Could not add application
Could not add application to the application database

anyone can help me out? thanks[/QUOTE]
 Does it happen with all applications? Did you type the command manually or selected an application from the list?

---

### Post by Burgundavia on 2005-06-08
Check your permission on the .local directory in your home dir. Sometimes they can get messed up.

Corey

---

### Post by hysun on 2005-06-08
To Alexander Kirillov: yes, it happens to all application

To Corey: !!! yes, the problem is just with .local file. its owner is root. after change owner back to the normal user, it works. 

So, why would this happen? My guess: maybe before the .local file was created, i installed some application with sudo and it creates some file association, hence created the .local directory.

thanks guys.

---

