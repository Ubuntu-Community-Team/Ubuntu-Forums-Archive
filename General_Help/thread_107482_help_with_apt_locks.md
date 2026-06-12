---
title: "help with apt locks"
date: 2005-12-23
forum: General Help
---

### Post by thermopyl on 2005-12-23
Hi

I have the following problem!!!

scott@ubuntu:~$ $sudo apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
scott@ubuntu:~$ $sudo apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I do not have synaptic open...can anyone help me please?

---

### Post by Perfect Storm on 2005-12-23
Do you have any other application or terminals running?

Edit: why do you have $ infront of sudo? It might be it.

---

### Post by thermopyl on 2005-12-23
DOH!

now where did that rogue $ come from!!??

thanks mate, sometimes you need someone to point out the obvious
:???:

---

