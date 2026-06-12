---
title: "no permission for root"
date: 2009-01-14
forum: General Help
---

### Post by shafi on 2009-01-14
Hello all,
one of my colleague did something strange to his laptop,
he wanted to grant permission for a folder but instead he entered the following command from root:

**chmod -R 777 /***
and after a restart he can not login to his computer.
I tried to login through recovery mode and it was successful but now there is no permission for the root to do something, any help?
thanks.

---

### Post by Titan8990 on 2009-01-14
This command:

chmod -R 777 /*


Will always leave a system inoperable. Typically the only fix is a fresh install.

Careful what commands you use as root.

---

