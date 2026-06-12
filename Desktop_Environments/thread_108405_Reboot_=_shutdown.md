---
title: "Reboot = shutdown"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Sef on 2005-12-26
When I go to reboot my computer, it says reboot, and then it shuts down instead of restarting.  What can I do to fix this problem? :confused:

---

### Post by dcstar on 2005-12-26
[QUOTE=Sef]When I go to reboot my computer, it says reboot, and then it shuts down instead of restarting.  What can I do to fix this problem? :confused:[/QUOTE]
What kernel version are you using?

---

### Post by Sef on 2005-12-26
I know it is 2.6.10 something.....without rebooting to find out, how can I find out which kernel I have?

---

### Post by Brent Dax on 2005-12-26
Open a terminal window (Applications | Accessories | Terminal), type "uname -a" , press Enter, and copy the line it prints into your reply.  On my laptop, I get:
```
Linux motoko 2.6.12-10-686 #1 Thu Dec 22 11:55:07 UTC 2005 i686 GNU/Linux
```
(My laptop is named "motoko".)

---

### Post by Sef on 2005-12-26
Linux jokat1 2.6.12.10-386 #1 Thu 22 Dec 11:37:10 UTC 2005 i686 GNU/LInux

---

### Post by Ramon on 2005-12-26
Look into youre bios of youre motherbord!!!

I had the same problem as you, and i solved it whit going into the bios and change the settings of the powermanegemant.

---

### Post by Sef on 2005-12-26
Ramon: Thanks.  It worked.    

I went into the powermanagement and changed 'Startup after Power Failure' to ON from Auto.

---

### Post by Sef on 2005-12-26
oops. duplicate post.

---

