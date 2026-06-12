---
title: "Stellarium-0.10.2"
date: 2009-03-29
forum: General Help
---

### Post by egrpioneer on 2009-03-29
Just compiled without issue, but synaptic still shows, and only loads version 0.9.1-4. Tried all methods that I could locate in this forum and elsewhere. But always reverts to version 0.9.1-4.
Looking for direction.

Thanks in advance!!!

---

### Post by rmls on 2009-04-02
Hi egrpioneer

I'm not sure exactly what you mean (and others with more knowledge
may correct me :) ) but if you have followed the instructions for 
compiling and installing Stellarium from source posted on this forum,
and it runs?.. 

Then when you go to synaptic and do a search for say stella the 
new version will probably be called unix (!) in the package name 
but the description section will show it as stellarium 0.10.2_i386 
or similar and marked as green for installed ...hope this helps......

Cheers
rmls

---

### Post by taurus on 2009-04-02
Did you install the new version to /usr/local/bin?

```
ls -la /usr/local/bin
```
Try removing the older version from the repos first and then see if you can run the new version that you've compiled from a terminal.

```
stellarium
```

---

