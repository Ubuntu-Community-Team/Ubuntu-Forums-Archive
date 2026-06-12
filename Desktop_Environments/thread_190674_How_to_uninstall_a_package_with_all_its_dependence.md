---
title: "How to uninstall a package with all its dependences?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by franestepona on 2006-06-06
Hi!
Happened so many times that i install a program and then i want to get rid of it. When the programs install also its dependences i want to uninstall them too, but it is pretty annoying to go to History, copy all the names and remove them using command line. Is there any way to uninstall a program directly from History or another easier way to uninstall the dependences? Can I search in the History to find out when I did install a certain program?

I have been tying to find the answer, if these features are not implemented in the program it could be an important thing to keep in mind for the next ubuntu release :)

Thanks in advance!

---

### Post by Ramses de Norre on 2006-06-06
Use aptitude, it holds a database of installed dependencies and removes them when they're not needed anymore. It has pretty much the same syntax as apt-get.

---

### Post by franestepona on 2006-06-06
Ok thanks! I am going to try that program from now on.

---

### Post by dudus on 2006-06-06
Is there a way to uninstall libs that no soft uses?

---

### Post by Ramses de Norre on 2006-06-06
you can use deborphan to list them and then manually purge them.

---

### Post by aysiu on 2006-06-06
For all the programs you installed before you started using *aptitude*, try *gtkorphan* to find those.

---

### Post by Ramses de Norre on 2006-06-06
That's quite a nice tool I didn't know about yet. But there are a few packages listed that don't seem orphaned to me.. can I be really sure all those packages are unneeded?

---

### Post by aysiu on 2006-06-06
"Orphaned" doesn't mean "unneeded."

It means no other packages depend on them. You have to look through them and decide for yourself whether they're needed or not.

---

### Post by Ramses de Norre on 2006-06-06
But orphaned libraries are no programs of their own, no? So it should be safe to remove any orphaned libraries?

---

### Post by aysiu on 2006-06-06
[QUOTE=Ramses de Norre]But orphaned libraries are no programs of their own, no? So it should be safe to remove any orphaned libraries?[/QUOTE] Actually, those are probably the ones you should keep. The "orphaned" libraries may not have programs that *depend* on them, but they may have programs that *use* them.

For example, AmaroK doesn't depend on MP3 codecs, but if you remove those codecs, you may no longer be able to play your MP3s.

---

### Post by Ramses de Norre on 2006-06-06
Good I asked :D

---

