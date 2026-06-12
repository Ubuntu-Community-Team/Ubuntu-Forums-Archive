---
title: "Howto debug kde"
date: 2006-08-14
forum: Desktop Environments
---

### Post by krisravn on 2006-08-14
Hey

Im using kubuntu in a multiuser environment, but I have some major problems with some kde programs, example konqueror keep crashing, so I wondering, if they is a log file to kde, where I can see whats going wrong. I need to be able to log every kde programs and it will also be nice if I can log when a user starts a program and when he/her close it again.

Regards
krisravn

---

### Post by asimon on 2006-08-14
You will find some diagnostic messages in ~/.xsession-errors .

With the program 'kdebugdialog' you can enable or disable debug output from various areas. And with 'kdebugdialog --fullmode' for every severity level you can define separately what should be done with the diagnostic messages of that level, and the same for each debug area. There is also the option to put all those messages in some log file.

---

