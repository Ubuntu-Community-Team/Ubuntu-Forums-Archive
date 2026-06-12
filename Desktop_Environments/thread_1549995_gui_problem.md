---
title: "gui problem"
date: 2010-08-10
forum: Desktop Environments
---

### Post by syedmuja on 2010-08-10
Hello I am using ubuntu operating system, recently I am getting one problem when i am using the system . system is automatically going to command line mode it is asking user name and password. After entering user name and password I can able to use the system only in command line mode. Again when i restart I am getting gui as usual. Please help me to resolve the problem.



from,
s.m. pasha,
Asst Professor,
SNIST,
HYDERABAD,
INDIA.

---

### Post by Zorgoth on 2010-08-10
When you are in command line mode, have you tried using both of these commands:

startx

EDIT: sudo service gdm --full-restart

The first will, if working correctly, bring up a graphical desktop.  The second will, if working correctly, bring up a login screen.

---

