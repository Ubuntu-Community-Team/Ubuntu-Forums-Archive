---
title: "Wondering if I can disable some services"
date: 2009-05-25
forum: General Help
---

### Post by mcgodx on 2009-05-25
Hi all,

I have been looking around lately for ways to speed up 9.04 (not that it's slow to begin with but I kinda don't like how there are a lot of services in there running in the background).

I was wondering why there are 3 different action scheduler services running (anacron, atd, and cron).  Is it possible to disable these three without ill effect?  Also I do not know how to check what actions are scheduled exactly as I have not done any personally.

I didn't know if Linux had any by default like to clear out temp folders or something like that.

Thanks

Mylan

---

### Post by B4RR13N705 on 2009-05-25
In system-->Administration, you have a Services menu, there you can disable the ones that you dont need.

---

### Post by cariboo on 2009-05-25
Do not disable the three services you mentioned, as it will lead to a none funtioning system. You can disable anything you don't need in System-->Preferences-->Startup Applications.

[list]
[*]anacron, can be used to execute commands periodically, with a  frequency
       specified in days.  Unlike cron[noparse](8)[/noparse], it does not assume that the machine
       is running continuously.  Hence, it can be used on machines that aren’t
       running 24 hours a day, to control daily, weekly, and monthly jobs that
       are usually controlled by cron. 
[*]atd run jobs queued for later execution
[*]cron daemon to execute scheduled commands
[/list]

The above deamons are important as they run a lot of functions that run in the background.

---

### Post by mcgodx on 2009-05-25
Thanks I'll leave those services be then.

---

### Post by oldos2er on 2009-05-25
The startup applications app doesn't show all services, but sysv-rc-conf will.

---

