---
title: "saving a file as executable?"
date: 2008-01-14
forum: Desktop Environments
---

### Post by dzuari on 2008-01-14
wats the .*** that i save a file as so it can be executable????

---

### Post by sjnovick on 2008-01-14
There is no file extension to make a file executable.  You can, however, make any file executable by changing the file property.

Open a terminal and type:

#     chmod +x filename

where filename is the name of your file.


If you want to do this using the file manager, then right-click on the file, choose properties and check the box marked "executable?".


To execute the file, just click on it from your file manager.  Or, from a terminal, type:

#     ./filename


Hope that answers your question.

---

### Post by stchman on 2008-01-14
> **dzuari said:**
> wats the .*** that i save a file as so it can be executable????

Having files be not executable is a great security feature of Linux.

---

