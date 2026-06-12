---
title: "Help with Phun"
date: 2008-12-16
forum: Gaming &amp; Leisure
---

### Post by g3brownsc on 2008-12-16
Hello all,
Trying to get Phun working 
[INDENT][/INDENT][http://www.phunland.com/wiki/Home](http://www.phunland.com/wiki/Home)
and I'm experiencing some strange behavior. The program starts, but I'm unable to liquefy anything without crashing it. 

My specs - 
8.10 Intrepid
Phun beta 4.22
Intel GMA X3100 integrated graphics

Searches on the forum yielded no help with this particular issue. 

Any help or advice would be awesome, thanks.

---

### Post by crazyfuturamanoob on 2008-12-16
Try an older version of phun.

---

### Post by Bölvaður on 2008-12-16
the version in the repos works well.... so I'd say get it via the synatpic

---

### Post by g3brownsc on 2008-12-16
Ahh I ended up sorting it out. I had complex water enabled, which requires shaders which my graphics card doesn't do. 
The staticky shapes were taken care of by running 
```
metacity --replace
```
before firing up phun and 
```
compiz --replace
```
when finished. Thanks for the help anyways.

---

