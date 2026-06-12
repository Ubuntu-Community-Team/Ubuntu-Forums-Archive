---
title: "how can i get loadable module information while booting of linux"
date: 2009-06-13
forum: General Help
---

### Post by dileep.kk on 2009-06-13
Hi all,
I am desparately trying to debug linux while booting to get loadable module information.But I am new to this so I need to know how kernel knows about the loadable modules while booting.
If kernel use any data structure to know  these informations ,how can i get it while booting .
 
 
Thanks in advance

---

### Post by Joeb454 on 2009-06-13
Thread moved to  General Help.

I can't remember how to do it myself, but if I recall correctly, you need to disable usplash to stop the Ubuntu loading image appearing :)

---

### Post by arnoldjames on 2009-06-17
> **Joeb454 said:**
> Thread moved to  General Help.

I can't remember how to do it myself, but if I recall correctly, you need to disable usplash to stop the Ubuntu loading image appearing :)
And how is this done?  Yes, I will look high and low to find it, but no joy quite yet.If you have a link or simple instructions, please post.  Thanks!

---

### Post by sdennie on 2009-06-17
I don't completely understand your question.  What specifically are you looking for?  The names of all the modules that kernel has available?  The names of the modules it's trying to load?  The names of the modules that are built into the initrd?

Joeb454s suggesting might be a good start.  The easiest way to select a kernel labeled "recovery mode" from the boot menu.  That will give you the most information during the boot process.

---

