---
title: "Permission problem"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Paul Chang on 2006-07-12
I am using Ubuntu 6.06 on both of my desktop and laptop. I have two accounts in both system. But I noticed that if I log into one accout, I also have full control to another accout. For example, I have account "A" and "B". When I log into account "A", I can read, write, delete any files belong to account "B". Does anyone have the same experience? 

Linux is a multi-user OS. If there is no permission from account "B", account "A" should NOT have any right to access the dirctories and files belong to account "B". right?

Does anyone know how to fix this problem? Thanks in advance.

---

### Post by scxtt on 2006-07-12
if A and B are in the same group and group permissions are set to ---rwx--- then you'll experience that ... you should probably give us some examples from your system instead of the generic "A" and "B" ...

---

### Post by Paul Chang on 2006-07-13
Thanks. I'll check the group permission first.

---

