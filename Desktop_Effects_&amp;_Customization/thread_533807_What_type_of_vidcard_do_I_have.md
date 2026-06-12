---
title: "What type of vidcard do I have"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by cudds on 2007-08-24
Loads of cool tutorials out there but they all depend on the type of vid card one has.
How do I find out? 

I think im running some intel driver or something :confused:

---

### Post by Inxsible on 2007-08-24
Open up a terminal and type in ```
lspci
```Look for nvidia or ATI or something like that.

---

### Post by Happy_Man on 2007-08-24
Go into System --> Administration --> Device Manager and look for it there. If you can't find it, enter the code ```
lspci
``` and see what that gives back for it.

In general, though, if you have an Intel driver, you should be OK.

---

