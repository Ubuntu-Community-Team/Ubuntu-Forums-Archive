---
title: "Anyone tried FreeMat - the matlab knockoff?"
date: 2007-12-26
forum: Education &amp; Science
---

### Post by slimdog360 on 2007-12-26
[http://freemat.sourceforge.net/wiki/index.php/Main _Page]("http://freemat.sourceforge.net/wiki/index.php/Main _Page")

I just went to use it but it wants qt4 and that will mess up my pretty zenwalk setup. I wanted to know if anyone has tried it before and whether its any good so that I don't mess up my current setup for no reason.

Becasue Im on slackware I dont have this pleasure but for those who dont know; there is a rpm on the site, I don't know if its in the Ubuntu repos but if not you can convert the rpm to a deb and install with ```
sudo alien FreeMat.rpm && dpkg -i FreeMat.deb
```

---

### Post by artesian_spring on 2007-12-26
How does freeMAT compare with octave?

---

### Post by slimdog360 on 2007-12-27
that's what I want to know

---

### Post by EaglemanBSA on 2008-02-09
Actually, I work with it quite a bit. It works really well, but if you're straight copying MATLAB scripts over, you might have to change a few small things. functions like fprintf and fscanf don't work precisely the same way, etc. Aside from the small subtleties, I haven't found anything I haven't been able to do in Freemat that I could do in MATLAB. I highly recommend it.

---

