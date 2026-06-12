---
title: "Ubuntu 7.10: recently automatic updates can't install one of the updates"
date: 2008-05-23
forum: Desktop Environments
---

### Post by pentolino on 2008-05-23
Hello,
I recently started having a strange problem with automatic updates in Ubuntu 7.10. When there is more than one package to update it updates all the package but one, and it refuses to update that package even if I launch it again.
For example, say I have to update:
package1, package2 and package 3.
I check all the three and start update; all apparently goes well, but after refresh it turns out that package2 has not been upgraded. So I double check that package2 is selected and start update again. Same thing, package2 is still there to be upgraded...
This is happening since a month or two, before everything worked fine.
I don't think that package database is somehow corrupted because using apt-get in the shell works like intended (that is upgrades package2 without any problem), so what? Is there a way I can "reset" synaptic to "factory" settings with not too much hassle?
Thanks for any idea.
Riccardo

---

### Post by warp99 on 2008-05-23
Sometimes there are dependency issues with the package manager that are not resolved with Synaptic and you have to drop to apt-get for resolution. It's an anomaly that happens every so often. 

Remember Ubuntu 32-bit supports 24,680 packages in the repositories, so an error is bound to happen with one of them

---

### Post by pentolino on 2008-05-23
Thanks for your feedback.
I understand there are many dependecies involved, but what sounds strange to me are three facts:
1) it happens very often since a couple of months (I would say almost always)
2) it happens even in quite simple updates (like the recent one for the famous ssh security hole, it had to upgrade 4-5 package and left one unupdated)
3) once I run update manager again it should have no trouble with just one package!

---

### Post by warp99 on 2008-05-23
> **pentolino said:**
> 
2) it happens even in quite simple updates (like the recent one for the famous ssh security hole, it had to upgrade 4-5 package and left one unupdated)

I can give the answer for that one. Because the package had to run an interactive script to check the ssh keys check against the blacklist the maintainers felt that user interaction was paramount versus the automated updater.

---

### Post by pentolino on 2008-05-27
Hello Warp,
thanks for your reply. I see your explanation but disagree :-)
Today I have a precise example: linux-ubuntu-modules-2.6.22-14-generic is the only package I have to update. Maybe it will request a reboot but surely it does not need user input.
Well automatic update won't install this package, no way :-( It simply does nothing and refreshes package list to show always the same package...
Synaptic doesn't list this package in the ones to be updated.
apt-get works ok as usual.
It seems something in synaptic went wrong.

---

### Post by Xiong Chiamiov on 2008-05-27
I would get into the habit of using
```

sudo aptitude safe-upgrade

```
If there are dependency problems, it will come up with a number of solutions and ask you for what you want to do.

---

### Post by pentolino on 2008-05-28
Thanks for the hint, I will try next time. 
But I would also like to know if there is a way to get synaptic working back :-)

---

