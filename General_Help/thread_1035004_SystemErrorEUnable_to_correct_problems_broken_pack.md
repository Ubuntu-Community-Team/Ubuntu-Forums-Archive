---
title: "SystemError:E:Unable to correct problems broken packages, Restricted Nvidia drivers"
date: 2009-01-09
forum: General Help
---

### Post by Urinemachine on 2009-01-09
Hello all,

Trying to get my desktop at work here going with the restricted drivers so I can run desktop effects.  On my home PC I just boot up, active restricted driver and away I go.  But I am getting an error here:

SystemError E:Unable to correct problems, you have held broken packages.

This is a wubi install of 8.10.  How do I fix this?

Thanks!

---

### Post by ajgreeny on 2009-01-09
I'm not completely sure if this works in a wubi install, but it sounds as if you have a broken package which if you want to use a gui fix would be synaptic, choose Custom Filters from the left panel options and then Broken to see what the problem is.  You can then choose the Edit > Fix Broken Packages menu to hopefully do just that.

If that doesn't work, I can not think of anything else, I'm afraid.

---

### Post by Urinemachine on 2009-01-09
I actually ran apt get from the terminal and saw a real error.. .it was something about a key not being correct and such.  I changed the sources from us.archive or archive.us to just archive.ubuntu.com... seems to work.

---

