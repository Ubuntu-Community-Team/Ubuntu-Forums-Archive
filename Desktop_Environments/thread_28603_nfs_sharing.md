---
title: "nfs sharing"
date: 2005-04-20
forum: Desktop Environments
---

### Post by arnieks on 2005-04-20
Hello,
Trying to get my ubuntu box to share a directory using nfs, so my dreambox can record movies to it.  I have installed nfs and required stuff, but I have two questions.
How do you make nfs start up automatically? ( in other distributions I have used chkconfig, or manually added links in rc3.d and 5.d)
What permissions do I set for the directory I want to share?

I have added the box in /etc/exports and did other recommended settings as given in the nfs HOWTO, but permissions weren't mentioned.

Thanks
Arnie

---

### Post by diebels on 2005-04-20
Adding link to /etc/rc2.d/ would work. Ubuntu's default runlevel is 2. Permissions is normal file permissions. You can just add a dreambox user or something that will have write permissions to the movies.

---

### Post by arnieks on 2005-04-21
[QUOTE=diebels]Adding link to /etc/rc2.d/ would work. Ubuntu's default runlevel is 2. Permissions is normal file permissions. You can just add a dreambox user or something that will have write permissions to the movies.[/QUOTE]
thanks,


Will I need an entry in my fstab as well?

---

### Post by icecube76 on 2005-06-12
how to make dreambox share ubuntu harddisk?
how to install cifs or nfs?

regards

---

