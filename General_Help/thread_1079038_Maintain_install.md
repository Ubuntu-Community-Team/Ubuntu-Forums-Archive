---
title: "Maintain install"
date: 2009-02-23
forum: General Help
---

### Post by paimon.soror on 2009-02-23
Hey guys,

I was wondering if there were any tips to maintain your linux install.  For example i know that the win guys have things like CCleaner, regcleaners, defraggers etc.  I know that the way linux's architecture is set up, fragmentation is very low so the need for a defragger is not necessary, but are there any programs that can help make sure things are "clean" and "in order"

Im really loving my ubuntu install and just looking for ways to make sure i'm treating her right haha.

Thanks

---

### Post by iaculallad on 2009-02-24
Here are some commands/list for you to do for maintenance purposes:

-Clean up partial package:

```
sudo apt-get autoclean
```

-Clean up the apt cache directory:

```
sudo apt-get clean
```

-Clean up any unused dependencies:

```
sudo apt-get autoremove 
```

---

### Post by paimon.soror on 2009-02-24
> **iaculallad said:**
> Here are some commands/list for you to do for maintenance purposes:

-Clean up partial package:

```
sudo apt-get autoclean
```

-Clean up the apt cache directory:

```
sudo apt-get clean
```

-Clean up any unused dependencies:

```
sudo apt-get autoremove 
```

Great thanks, I knew about autoremove but forgot about the former two.  So I take it other than these there really isn't much need for "garbage collection" in a sense vs microsoft boxes?

---

### Post by taurus on 2009-02-24
Also keep your eyes on your log files in /var/log.  Remove those backup ones since you don't need them.  Meanwhile, /var/backups can take up a bunch of space on your harddrive if you have a backup app running with cron (crontab).

---

