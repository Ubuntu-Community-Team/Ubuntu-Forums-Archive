---
title: "Status LED for pcs available in the network"
date: 2012-12-07
forum: Desktop Environments
---

### Post by tor30 on 2012-12-07
Hello,

does someone know a possibility to create maybe status LED in the gnome panel / status bar , kde panel / status bar, gkrellem, superkaramba, plasma if specific pcs are available in the local network.

(I want to check if one can succcesfully ping a pc, the result should be green, and if not red,...)

Further Network monitoring is not necessary for me.

Any hints? Code fragments? Ideas?

Thanks

Torsten

---

### Post by Kirk Schnable on 2012-12-07
Have you thought about using Conky? It can overlay information on your desktop which you can generate with bash scripts running certain commands (attempting to contact your remote machines, for instance). Might be a starting point worth your consideration.

---

### Post by tgalati4 on 2012-12-08
I use rwho (with ruptime) and a zenity script:

[http://ubuntuforums.org/showthread.php?t=1417095&highlight=zenity](http://ubuntuforums.org/showthread.php?t=1417095&highlight=zenity)

I've been running it for several years.

---

