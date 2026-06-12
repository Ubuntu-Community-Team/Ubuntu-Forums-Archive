---
title: "&quot;Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)&quot;"
date: 2006-07-26
forum: Desktop Environments
---

### Post by aaronshaf on 2006-07-26
I get this when I try to use apt-get:

[INDENT]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/INDENT]

I've tried apt-get clean to no avail. How can I unlock it?

---

### Post by llamakc on 2006-07-26
Is Synaptic, Adept, Update Manager, Aptitude, or DSelect running?

Make sure with the command (from the terminal) `ps aux` or `pstree`

---

### Post by chalex on 2006-07-26
To unlock it, close the application that's using the package database.

---

