---
title: "How can I put &quot;emerald --replace&quot; in the start-up?"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by Starrfoxx on 2007-09-22
I've got a few emerald themes, and for now the only way I can get them to activate is by manually opening a command line with ALT+F2 and then typing "emerald --replace".  Is there anyway to put this in the startup, so that it is automatic?  I did go under Preferences/Sessions to put something there, but that didn't work.

---

### Post by Mongo5000 on 2007-09-23
You just have to go into sessions and add this to startup.

```
compiz --replace -c emerald
```

---

### Post by Starrfoxx on 2007-09-28
I tried that, but no luck.  I already have "compiz --replace" in there, and that works.  I tried your line separately, I tried "emerald --replace" separately, and I tried changing my existing "compiz --replace" command to match yours.  No luck.

---

### Post by erfahren on 2007-09-28
Maybe you could try starting emerald with a delay. see the "make compiz fusion load fast at start up" part and the end of this post: [http://ubuntuforums.org/showpost.php?p=3026765&postcount=2](http://ubuntuforums.org/showpost.php?p=3026765&postcount=2)

---

### Post by dpar on 2007-09-28
In your compiz settings manager go to the window decoration plugin and type in 'emerald' under command. That will start compiz with emerald.

---

### Post by axyd on 2008-05-17
> **dpar said:**
> In your compiz settings manager go to the window decoration plugin and type in 'emerald' under command. That will start compiz with emerald.

using just emerald command didnt work, but  emerald --replace   worked like a charm

---

### Post by torchfire on 2008-05-18
> **axyd said:**
> using just emerald command didnt work, but  emerald --replace   worked like a charm

Thanks, all.  That worked for me, too. 

Torch

---

