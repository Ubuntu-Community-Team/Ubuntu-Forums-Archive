---
title: "Kubuntu 14.04 doesn't update to 14.04.02?"
date: 2015-06-30
forum: Desktop Environments
---

### Post by algar2 on 2015-06-30
I don't get hardly any updates from Muon Update Manager. Shouldn't the upgrade for 14.04.02 appear at least?

---

### Post by PaulW2U on 2015-06-30
Hello algar2, in a terminal window type the following command so we can see exactly what you have at present.

```
lsb_release -a
```

---

### Post by deadflowr on 2015-06-30
No.
It is comes like a normal update.
Try:
```
lsb_release -a
```
it'll show what point release you are currently on.

Ninja'd on the code...

---

### Post by algar2 on 2015-06-30
Oops, seems like I'm running [COLOR=#000000]14.04.2 

[/COLOR]"about System" and SysInfo showed it simply as 14.02[COLOR=#000000]
[/COLOR]

---

### Post by PaulW2U on 2015-06-30
> **algar2 said:**
> Oops, seems like I'm running 14.04.2 

I thought that you might be.

If you continue to update then you'll get 14.04.3 and 14.04.4 in due course. Ubuntu point releases aren't like Windows Service Packs. Just update when updates arrive and you always be running the latest and greatest. :)

---

### Post by ajgreeny on 2015-06-30
There is, however, still a difference between your installation and a new installation of 14.04.2.

Normal updating does not upgrade all the packages of the hardware enablement stack, but you do not need to concern yourself about that unless you have really new hardware and some of it is not working very well.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

