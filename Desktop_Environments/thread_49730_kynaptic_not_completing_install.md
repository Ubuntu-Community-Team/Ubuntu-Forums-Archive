---
title: "kynaptic not completing install"
date: 2005-07-17
forum: Desktop Environments
---

### Post by coolclassic on 2005-07-17
kynaptic has failed to finnish the install process. Now when I try to complete this I get the following error:

Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I solve this ?

---

### Post by Evera on 2005-07-17
[QUOTE=coolclassic]kynaptic has failed to finnish the install process. Now when I try to complete this I get the following error:

Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I solve this ?[/QUOTE]
 Do you have two instances of kynaptic open, or did you try something like apt-get from konsole?

---

### Post by coolclassic on 2005-07-17
I closed kynaptic down before it completed an install it was taken an age to complete. The problem was that a package I was installing was looking for an yes/no answer kynaptic was not giving this option and frozed.
I solved the problem by using ksysguard which should knaptic still running. I closed it down which solved the kynaptic problem.

My other problem was sorted by:

sudo dpkg --configure -a
This allowed the completion of the install and I was able to answer yes to the option.

---

