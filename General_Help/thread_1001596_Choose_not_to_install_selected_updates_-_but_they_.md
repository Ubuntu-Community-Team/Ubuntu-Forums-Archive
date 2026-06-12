---
title: "Choose not to install selected updates - but they keep appearing"
date: 2008-12-04
forum: General Help
---

### Post by stevebond001 on 2008-12-04
Hi
I have recently received some updates for Intrepid through the update manager.  However, there are some updates which I have chosen not to install as they are connected with Evolution, which i do not use and have de-installed. However, these updates still show up in the update manager as ready for installation.

Can I hide or remove these updates as I don't want them?

TVM in advance

---

### Post by Peter09 on 2008-12-04
They most probably keep appearing because the packages are still installed. You could remove them using synaptic but beware - some of the evolution libraries are used by other applications, so although you may have removed Evolution, its libraries may still be in use.

My advise would be to upgrade them, that would stop them bothering you.

It might be worth doing 

```
sudo apt-get autoremove
```

I think that will remove any packages that you are not using.

---

### Post by stevebond001 on 2008-12-04
Peter09
Thanks for the advice - I think I'll follow it and just install the packages, then run the **sudo apt-get autoremove** command

---

