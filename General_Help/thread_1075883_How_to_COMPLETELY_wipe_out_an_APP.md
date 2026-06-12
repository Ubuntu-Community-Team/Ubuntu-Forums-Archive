---
title: "How to COMPLETELY wipe out an APP"
date: 2009-02-20
forum: General Help
---

### Post by its_jon on 2009-02-20
Hi... I am struggling with a broken app

Its Musescore 0.9.4 ibelx 64bit.

Its broken and I want to remove it completely so I can reinstall it fresh.

Whenever I get synaptic to perform a complete removal and then I reinstall it.... I get the broken version back ?!

What am I doing wrong ?.

Thanks..

---

### Post by issih on 2009-02-20
Couple of thoughts, generally the complete removal is meant to take the config files as well as the actual application,which should give you a clean slate, but I'm not sure how reliable it is.

Either way it could be that the actual version in the repository is broken, did it ever work?

One final idea, make sure you remove any packages that were installed as dependancies (i.e. run "sudo apt-get autoremove") in case the broken bit is in a package installed as a dependancy which is not being removed..

Other than that I'm a bit lost

---

### Post by jerome1232 on 2009-02-20
Summarizing issih comments into an apt-get command (as nice as synaptic is I find myself always using apt-get instead)

This should remove the package, it's config files, and any dependencies it's dragged in along with itself along with their configurations.

```
sudo apt-get autoremove --purge packagename
```

---

### Post by its_jon on 2009-02-20
Thanks for the reply I performed the task in a terminal....

A LOT more comprehensive !!!

I was certain that this would fix it as it took much more time to remove and also more time to reinstall.....

However....

The App is still broken....

The same version did work until I altered a config setting. The setting was to reload previous session (last session) of work instead of loading the demo file all the time.
After doing this I have lost the main functionality of the program after it loads....

My guess is that it has saved a corrupt config file somewhere that fresh installations are reading...
As a Linux new person :) ... I really don't know where to look... and my bug is unfortunately one of many for the dev team so just hoping the Ubuntu community may be able to shed a suggestion or two...

many thanks
John
Scotland.

---

### Post by scouser73 on 2009-02-20
> **jerome1232 said:**
> Summarizing issih comments into an apt-get command (as nice as synaptic is I find myself always using apt-get instead)

This should remove the package, it's config files, and any dependencies it's dragged in along with itself along with their configurations.

```
sudo apt-get autoremove --purge packagename
```

Excellent tip, have been looking for this for a while now, thank you.

---

