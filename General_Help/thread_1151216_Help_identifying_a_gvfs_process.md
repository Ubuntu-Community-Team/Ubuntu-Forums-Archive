---
title: "Help identifying a gvfs process"
date: 2009-05-06
forum: General Help
---

### Post by risingsun on 2009-05-06
Hi, I was just checking through the process list using ps x and I was curious as to what:

/usr/lib/gvfs/gvfsd-trash --spawner :1.3 /org/gtk/gvfs/exec_spaw/0

and 

/usr/lib/gvfs/gvfsd-trash --spawner :1.3 /org/gtk/gvfs/exec_spaw/1

could be processes for? I can't readily identify what they're for (I'm not sure what gvfs is either but since there seem to be many I assume it's part of the gnome desktop or somesuch.) Are they to do with gtk as in the gui thing?

Many thanks for any help offered. :)

---

### Post by BslBryan on 2009-05-06
Firstly, hello to you, risingsun. :-)

That process means that a lot of files were moved to the trash recently.  

It can also mean that there are multiple trash files, for some reason, so any time you send one item to the trash, it gets sent to multiple places.

Also, it seems that Avant Window Navigator sends multiple things to the trash that get deleted instantly, so if you have that enabled, and this process bothers you, simply disable it and it should solve your problems.  

Best to you.  :-)  I hope I've helped.

---

