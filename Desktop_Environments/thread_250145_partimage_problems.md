---
title: "partimage problems"
date: 2006-09-03
forum: Desktop Environments
---

### Post by CyberCod on 2006-09-03
I am trying to copy my ubuntu installation to a different partition.

I want to be sure I have set up fstab and menu.lst and be sure I can boot up into the duplicate partition before I remove the original. 

I have seen a post using 

```

sudo cp -a /mnt/oldubuntu/* /mnt/newubuntu/

```

substituted by my specific mount points.

But it's problem is that it tries to copy the /media folder and cannot copy itself onto itself.

It seems to hang at this point in terminal.  Of course I cannot unmount the partitions, else I cannot copy to them.

Partimage is having trouble as well.

Anyone have any ideas or comments?

---

### Post by Breaker_324 on 2006-09-03
Go and eat a Caca!:)

---

