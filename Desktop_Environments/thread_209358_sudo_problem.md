---
title: "sudo problem"
date: 2006-07-05
forum: Desktop Environments
---

### Post by cotcot on 2006-07-05
After reformatting my separate /home partition because of a filecheck error I lost the home directory of the user and also its sudo rights.
I recreated the user from recovery mode (adduser -m user) but this does not give sudo rights. It is a new installation. I can/could not loose important data. 

How can i give the user sudo rights from terminal (recovery mode)  ?

Thanks

---

### Post by aysiu on 2006-07-05
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by cotcot on 2006-07-05
Problem is solved (addgroup username admin)Thanks !

---

