---
title: "Error when trying to update"
date: 2005-09-05
forum: Desktop Environments
---

### Post by zarathustra on 2005-09-05
Whenever I try to run apt-get to check for updates from the repository I get this error:

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


What does this mean and how do I fix it?

---

### Post by woedend on 2005-09-05
[QUOTE=zarathustra]Whenever I try to run apt-get to check for updates from the repository I get this error:



What does this mean and how do I fix it?[/QUOTE]
 usually i get that when i have synaptic or another instance of apt based working.  make sure its the only one on.  if you still get error message, do a clean restart and do only apt-get and tell me if you get same error.

---

### Post by zarathustra on 2005-09-05
It's worked thanks, I was pretty sure I hadn't got anything else open and I usually get a different error message when I do.

---

