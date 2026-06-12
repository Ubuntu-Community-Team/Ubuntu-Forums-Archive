---
title: "issues with possible broken packages?"
date: 2009-06-14
forum: General Help
---

### Post by Dj TweeX on 2009-06-14
so i was installing a DS emulator "desmume" and my system froze, (Which it often does) so i turned it back on & tried to run the useual

```
sudo dpkg --configure -a
```

to fix it but i get this,

```
Setting up libgtkglext1 (1.2.0-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgtkglext1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of desmume:
 desmume depends on libgtkglext1; however:
  Package libgtkglext1 is not configured yet.
dpkg: error processing desmume (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtkglext1
 desmume

```

so i tried to configure the lib first as it says its a dependency of desmume

so i try 

```
sudo dpkg --configure libgtkglext1
```

but i get this!

```
Setting up libgtkglext1 (1.2.0-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgtkglext1 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libgtkglext1
```

i dont know what to do! 
Any help please??

~~Gabe~~

---

### Post by lamego on 2009-06-14
Try removing libgtkglext1 first.

---

### Post by Dj TweeX on 2009-06-14
i thought i tried that... haha
but yea i just tried to purge it, which didnt work but it kind of nudged its status to half-installed & i was able to --reinstall from there. thank you.

---

