---
title: "Unrar"
date: 2005-10-25
forum: Desktop Environments
---

### Post by vital_101 on 2005-10-25
I've recently tried to install unrar on my system, but I'm getting this error:

$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

Is there a way to fix this?

/vital_101

---

### Post by Appolusionist on 2005-10-25
You might not have the correct repositories listed to get that installed. What do you have listed in /etc/apt/sources.list?

---

### Post by az on 2005-10-25
There are two versions of unrar and one for rar.  There is one GPL unrar in universe and the others are in multiverse because they are not free-libre software (they are freeware)

---

### Post by vital_101 on 2005-10-25
Thanks, I ended up figuring it out.

---

