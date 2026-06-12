---
title: "restricted repositories.. and ati driver."
date: 2005-10-01
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-01
Hi.
I had to uninstall the restricted repositories to get the driver installed.
Does this mean i have to leave them uninstalled..?
thanx

---

### Post by mlomker on 2005-10-02
> I had to uninstall the restricted repositories to get the driver installed.


Do you mean the restricted-modules package?  Both of those packages contain the fglrx driver, so you should only install one of them.

If you need the other drivers (wifi and whatnot) that come with the restricted-modules package then you should use that instead.

---

### Post by floyd27 on 2005-10-03
ok..
im sure you have the name right and im wrong..
so i reinstalled them and lost the driver...
after doing the process over again i got the driver back and wonder what to do now?
i dont understand what is going on..really im a little lost here..:confused: 
thanx

---

### Post by mlomker on 2005-10-03
You are probably better off using the restricted-modules package.  It'll get update whenever they update the kernel whereas the xorg package might not.

I set my kernel as 'locked' in synaptic so that it won't update to solve the issue.

---

### Post by floyd27 on 2005-10-03
thanx for your reply..
those r the ones i re-installed and lost my drivers..
im not sure what they do or why i would need them..
right now they (non free and free modules) are uninstalled.

Is it ok to leave it like that?

---

