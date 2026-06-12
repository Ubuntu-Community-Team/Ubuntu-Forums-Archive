---
title: "Launcher for Java Applications"
date: 2010-11-23
forum: Desktop Environments
---

### Post by mrkeef on 2010-11-23
I use VUE, a mind-mapping tool written in Java.

Previously I had a desktop launcher /opt/VUE/VUE.jar and that happily opened it. Since 10.10 it won't launch VUE. 

Can someone please tell me what command I should use?

THanks

Keith

---

### Post by joehillen on 2011-03-03
Try this:

Edit the launcher and in the command field put:

```
cautious-launcher /opt/VUE/VUE.jar java -jar

```

You might get an error that the executable bit in not set for the jar file.

---

