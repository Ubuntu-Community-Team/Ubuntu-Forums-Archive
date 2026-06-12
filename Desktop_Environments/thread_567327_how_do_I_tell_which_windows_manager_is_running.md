---
title: "how do I tell which windows manager is running?"
date: 2007-10-04
forum: Desktop Environments
---

### Post by sdahlin on 2007-10-04
How do I tell which windows manager is running?  I am getting a problem where all my windows open up in the upper left corner.

I am running Ubuntu 7.05, Gnome (I believe).

Thanks,
Seve

---

### Post by happysmileman on 2007-10-04
> **sdahlin said:**
> How do I tell which windows manager is running?  I am getting a problem where all my windows open up in the upper left corner.

I am running Ubuntu 7.05, Gnome (I believe).

Thanks,
Seve

the default Window manager for GNOME is Metacity, so it's highly likely that you're using it.

That is, unless you're using Desktop effects, which change the WM, desktops effects would be Beryl, Compiz or Compiz-fusion

---

### Post by sdahlin on 2007-10-04
I guess the question remains: how to I tell?  Do I need to run "ps" or is there some standard place to find that out?

Thanks,
Steve

---

### Post by notwen on 2007-10-04
Try the following commands to narrow it down.

```
ps aux | grep Beryl
```
```
ps aux | grep Compiz
```
```
ps aux | grep Metacity
```

Which ever ones comes back w/ a running process is what you have and are currently running. =]

---

### Post by rsambuca on 2007-10-04
You can also just look in your System Monitor!

---

### Post by sdahlin on 2007-10-04
Apparently none of the 3 are running?  Can I be running without a Windows Manager?

Thanks,
Steve

---

### Post by jimerickso on 2007-10-06
yes but it's not much fun.

---

### Post by rsambuca on 2007-10-06
Post a screen shot of your "System Monitor - Processes" tab.

---

