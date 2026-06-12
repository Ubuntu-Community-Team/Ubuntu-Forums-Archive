---
title: "Default load up screen; How to keep Unity as default instead of KDE?"
date: 2012-12-17
forum: Desktop Environments
---

### Post by bigred1978 on 2012-12-17
Good day,

Depending on the task at hand I like to sometimes alternate between either the default Unity desktop interface once logged in and on other occasions I like to login using KDE.

I installed KDE desktop with no trouble and set it up when logged in initially with no issues.

My question is:

Since I've installed the KDE desktop package everytime i turn on my computer and Ubuntu loads up the KDE login page/screen comes up rather than the Ubuntu Unity login screen.

How can I make the default Ubuntu login screen/page my default?

Any help appreciated, thank you.

:p 

P.S. : I'm currently using Ubuntu 12.04 LTS.

---

### Post by zombifier25 on 2012-12-18
Type this command:
```
sudo dpkg-reconfigure lightdm
```
then chose lightdm.

---

### Post by bigred1978 on 2012-12-23
Thanks.

---

