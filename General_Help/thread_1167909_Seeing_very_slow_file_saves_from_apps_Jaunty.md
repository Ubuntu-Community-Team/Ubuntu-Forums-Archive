---
title: "Seeing *very* slow file saves from apps Jaunty"
date: 2009-05-23
forum: General Help
---

### Post by kansas_plainsman on 2009-05-23
Since I upgraded to Jaunty I am seeing extremely slow file saves.  The app will actually dim out for up to half a minute - then finally the file save dialog will show up.  Any ideas what's going on?

---

### Post by cariboo on 2009-05-23
HAve you got anything else running that is using a lot of cpu cycles? Have a look at System-->Administration-->System Monitor-->Process or on an Apllication-->Accessories-->Terminal and type:

```
top
``` 

and note if there is a process that is using a lot of cpu cycles.

---

### Post by kansas_plainsman on 2009-05-23
Thanks for the reply.  TOP showed nothing out of the ordinary, but in further googling I found a reference to tracker - the indexing program.  Removing THAT solved the problem.

Apparently I have a sufficient number of small files to choke tracker - setting the program's defaults had little effect, so I uninstalled it - now I am getting normal performance once more.

---

