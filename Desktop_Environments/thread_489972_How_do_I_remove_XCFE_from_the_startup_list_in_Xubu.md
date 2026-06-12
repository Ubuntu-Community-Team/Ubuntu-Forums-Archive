---
title: "How do I remove XCFE from the startup list in Xubuntu?"
date: 2007-07-01
forum: Desktop Environments
---

### Post by Luigi239 on 2007-07-01
I am trying to remove XCFE from the startup items in Xubuntu, as I would rather just use ssh in the terminal. How can I do this?

Thanks :)

---

### Post by scxtt on 2007-07-01
you don't want X to start after you boot?  what display manager are you using [ gdm, kdm, xdm]?

---

### Post by kerry_s on 2007-07-02
**sudo killall gdm**

---

### Post by scxtt on 2007-07-02
and all that's gonna do is kill it for the current session ...

(s)he'll probably want to remove **lrwxrwxrwx 1 root root  13 2007-06-25 08:04 S99?dm -> ../init.d/?dm** from /etc/rc2.d/ ...

---

### Post by kerry_s on 2007-07-02
for permanent i would just uninstall it.

---

### Post by scxtt on 2007-07-02
nah, just remove it from the run-level directory you boot into, generally 2 for ubuntu (who -r) ... both gnome and kde have gui boot script editors, it's as simple as unchecking a box ...

---

### Post by Luigi239 on 2007-07-02
> **scxtt said:**
> nah, just remove it from the run-level directory you boot into, generally 2 for ubuntu (who -r) ... both gnome and kde have gui boot script editors, it's as simple as unchecking a box ...

That sounds easy, but where is the option? How do I navigate to it?



Thanks everybody. :)

---

### Post by scxtt on 2007-07-02
**cd /etc/rc2.d/**
[ this is the directory where the boot scripts for runlevel 2 are ]
**ls -l**
[ to see a listing of files in the directory ]
**rm S99kdm**
[this will remove the link to /etc/init.d for the display manager ]

you can post the output of **ls -l** before doing the rm if you want to be sure which one you want to remove ... i'm not sure if you have gdm, kdm, or xdm ...

---

