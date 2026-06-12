---
title: "How to run jar executable file with mouse click?"
date: 2011-11-20
forum: Desktop Environments
---

### Post by ravi_joshi on 2011-11-20
Hi, 
Unlike in windows, user can run jar executable file just by mouse click. We don't need to run it through terminal (java -jar myjarfile.jar).
How to set my Ubuntu to run directly from mouse click?

Please help.

Thank you.

---

### Post by Morbius1 on 2011-11-20
Open Nautilus with root privileges to the following location:
```
gksu nautilus /usr/share/applications
```Right click on "wine" 
Change the "Command" from this:
> cautious-launcher %f wine start /unixTo this:
> wine start /unixClose it and double click away.

---

### Post by Morbius1 on 2011-11-20
My sincerest apologies. That was a totally incoherent answer. It's been a rough week. The process was correct but the file was not:

Right click on whatever java runtime launcher you have in /usr/share/application and remove "[COLOR=Blue]**cautious-launcher %f**[/COLOR]"

---

