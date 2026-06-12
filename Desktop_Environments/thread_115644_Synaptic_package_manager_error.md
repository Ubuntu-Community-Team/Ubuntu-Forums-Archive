---
title: "Synaptic package manager error"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Dark Damo on 2006-01-11
> The following problems were found on your system:
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


> damo@OMG:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
damo@OMG:~$


Eh whats wrong?

---

### Post by newuser111 on 2006-01-11
type gedit /etc/apt/sources.list in a console and paste the contents of your sources.list file here

dont change anything

---

### Post by southernman on 2006-01-11
Not sure about how to fix your problem but try this to read/edit your sources.list:

> sudo nano /etc/apt/sources.list

You'll be prompted for your password. Enter this and have a look at your file.

HTH's in some way

---

