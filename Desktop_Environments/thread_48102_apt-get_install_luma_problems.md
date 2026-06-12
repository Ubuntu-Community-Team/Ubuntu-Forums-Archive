---
title: "apt-get install luma problems"
date: 2005-07-11
forum: Desktop Environments
---

### Post by blacksun on 2005-07-11
(from ubuntu rep)
after apt-get install luma && luma I get:
blacksun@HYDRA:~$ luma
Traceback (most recent call last):
  File "/usr/bin/luma", line 42, in ?
    startApplication()
  File "/usr/bin/luma", line 30, in startApplication
    gui = MainWin(None)
  File "/usr/lib/luma/base/gui/MainWin.py", line 32, in __init__
    MainWinDesign.__init__(self, parent)
  File "/usr/lib/luma/base/gui/MainWinDesign.py", line 599, in __init__
    self.taskStack.setSizePolicy(QSizePolicy(5,7,0,0,self.taskStack.sizePolicy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type
blacksun@HYDRA:~$

If i install luma on debian (with debian sources) it installs fine and runs fine.
whats the problem??

---

### Post by Abhi Kalyan on 2006-11-14
Hi got a question,
When i try to add objects to ldap through luma its asking for authentication.
How is this to be done?
Please throw in some pointers when possible.
Cheers
All the best 
Sincerely
Abhi Kalyan

---

