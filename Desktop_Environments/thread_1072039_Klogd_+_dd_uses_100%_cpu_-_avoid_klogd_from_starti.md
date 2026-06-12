---
title: "Klogd + dd uses 100% cpu - avoid klogd from starting"
date: 2009-02-17
forum: Desktop Environments
---

### Post by afonteijn on 2009-02-17
I just installed Xubuntu 8.10 on a p4 2.8ghz with 512mb memory. Soon after starting up the service klogd and dd start to use almost 100% of the cpu. I checked several forums, but the only workaround (I know it's not a great solution) is to kill klogd (sudo /etc/init.d/klogd stop). This does solve my problem, but I would like to make the change permanent. How would I do this? 

Of course, if anybody of you knows how to get klogd to act normally, please let me know. I read at several forums that this is a bug that might be corrected soon... I'll keep my fingers crossed! :D

Oh, and before I forget, I did not have this problem under Kubuntu 8.10 on the same PC.

---

### Post by dzyubam on 2009-03-26
I'm having the same problem in Ubuntu 8.10. I have an Intel Core 2 Duo 2.0Ghz proc and it's using more than 50% of it with dd and klogd running almost from the system start. Never had this problem when running Ubuntu 8.04. Any ideas?

---

### Post by dzyubam on 2009-03-26
I found a fix:
[http://ubuntuforums.org/showpost.php?p=6189105&postcount=7](http://ubuntuforums.org/showpost.php?p=6189105&postcount=7)

Updating the kernel helped.

---

