---
title: "Uninstalling Applications"
date: 2010-08-04
forum: Desktop Environments
---

### Post by mgthantzin on 2010-08-04
I've recently tried some applications on my Ubuntu and now I wish to uninstall some of them. What's the neatest way to do the task?

I'm abit new with Ubuntu.

Thanks.

---

### Post by claracc on 2010-08-08
The easiest way is through synaptic:

System --> administration--> software manager synaptic (introduce password), you look for the package you want to uninstall, you select it and in menu package, select mark to uninstall (completely, also quits configuration files).

---

### Post by mgthantzin on 2010-08-15
Thank you. I will try that.

---

### Post by dagdeniz on 2010-08-15
However keep in mind that Synaptic is not very good at tracking orphaned packages (I mean, you install xyz with ten dependencies and when you uninstall it, synaptic does not remember all of them and removes, say, three of them). Although Synaptic is efficient when installing packages, I would advise Aptitude for uninstallation (via command line): 

```
sudo aptitude remove xyz
```

and if you want the uninstall completely (wiping configuration, too):

```
sudo aptitude --purge remove xyz
```

---

### Post by mgthantzin on 2010-10-30
> **dagdeniz said:**
> However keep in mind that Synaptic is not very good at tracking orphaned packages (I mean, you install xyz with ten dependencies and when you uninstall it, synaptic does not remember all of them and removes, say, three of them). Although Synaptic is efficient when installing packages, I would advise Aptitude for uninstallation (via command line): 

```
sudo aptitude remove xyz
```and if you want the uninstall completely (wiping configuration, too):

```
sudo aptitude --purge remove xyz
```

You have pointed out my main concern. Yeah, it happens in Windows environment, too, where it doesn't uninstall everything it installed. Anyway, thanks for the input. I really appreciate it.

Cheers~

---

