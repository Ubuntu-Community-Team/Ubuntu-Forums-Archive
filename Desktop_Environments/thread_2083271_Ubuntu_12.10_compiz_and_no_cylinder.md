---
title: "Ubuntu 12.10 compiz and no cylinder"
date: 2012-11-12
forum: Desktop Environments
---

### Post by editheraven on 2012-11-12
I have installed ubuntu 12.10 on my new laptop. It runs compiz ok, but i cannot find in the menu the opcion for cylinder. In fact i think that no compiz-plugins-extra items are shown in the menu.

Why? My graphics processor is part of the cpu and i get all the effects without any other drivers.

le : note that "glxinfo | grep direct" outputs : direct rendering : Yes.

---

### Post by editheraven on 2012-11-12
any idea?

---

### Post by Frogs Hair on 2012-11-12
The compiz-plugins-extra appear in synaptic and I have them installed. Some plugins have been omitted due to developer workload and the location of some settings has changed. I am not finding the cylinder but I may have not looked in the right place either.

---

### Post by editheraven on 2012-11-14
You mean that for Ubuntu 12.10 is not the same build of compiz package than the one for Ubuntu 12.04 lts?

---

### Post by grahammechanical on 2012-11-14
You best read what the developers say:

[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/]("http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/")

Each version of Ubuntu uses different repositories. And that is because the packages are different.

For example, Precise has Linux kernel 3.2.0. Whereas Quantal has Linux kernel 3.5.0. Which Precise will not get until the end of January. But Raring Ringtail which is under development at the moment already has Linux kernel 3.7.0.

This affects all the bits and pieces that make up Ubuntu. If anyone thinks that these guys are not working hard then look at the full blog,

[http://smspillaz.wordpress.com/]("http://smspillaz.wordpress.com/")

and wait until you get down to **Apology** posted on December 25, 2011.

Regards.

---

