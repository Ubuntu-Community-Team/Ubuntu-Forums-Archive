---
title: "Quit Button Logs Out, but doesn't show the restart/shutdown/logout options"
date: 2009-03-15
forum: General Help
---

### Post by faustism on 2009-03-15
When I click the quit button (in the applications menu or on the top right) it brings me to the login screen and doesn't show me the shutdown, restart, log off, and switch user options.

Any ideas on what might solve this problem?

---

### Post by ellgor on 2009-03-15
Hi,

Had similar problem, turned out that the "gnome-power-manager" had been disabled/corrupted somehow, bit of a bugger to uninstall and reload it, but I did.

Regards, Ellgor.

---

### Post by faustism on 2009-03-15
i tried re-installing (with synaptic) the following packages:
```
gnome-power-manager
powermanagement-interface
laptop-mode-tools
powermgmt-base
acpid
lshw
apmd
libapm1
```

I restarted my computer and I still have the same problem.

How do you reload it?

---

### Post by faustism on 2009-03-15
would the fact that I'm using xfce make a difference?
(idk if you are using gnome)

---

### Post by ellgor on 2009-03-16
Hi again,

It also turns out that part of "Hal" (hardware abstraction layer?) wasn't installed, "libhal-dev", to be precise, check that out!

Regards, Ellgor.

---

### Post by faustism on 2009-03-16
thanks for the reply. I tired re-installing most of the hal packages including the one you said and I am still having the problem.

---

### Post by perrti-y02 on 2009-03-16
Did you start of from Xubuntu or Ubuntu?

---

### Post by faustism on 2009-03-16
xubuntu.

It didnt stop working. it just never worked

---

### Post by faustism on 2009-03-18
yesterday I finally broke down and reinstalled Xubuntu. Now my problems is solved. Must have been an error on install. Thanks for your help

---

