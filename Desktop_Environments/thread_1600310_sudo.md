---
title: "sudo"
date: 2010-10-18
forum: Desktop Environments
---

### Post by emir tel on 2010-10-18
i ran chmod 777 for a certain folder..
from then on I can't log in even as a root
if linux is about security, this makes me wonder security from who
this is my computer
i am the only user
how to fix that nasty reply : must be setuid ?

---

### Post by cj.surrusco on 2010-10-18
You probably made a mistake and executed the command on files that cannot be changed to 777, they must be left at 775. Are you receiving any errors specifically when you try to log on?

---

