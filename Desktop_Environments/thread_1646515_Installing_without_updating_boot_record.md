---
title: "Installing without updating boot record"
date: 2010-12-16
forum: Desktop Environments
---

### Post by ingeva on 2010-12-16
A few days ago I installed Ubuntu 10.10 Desktop edition.
The install was OK, but it didn't give me any choice about updating the boot record.
The result, of course, is that my permanent, tested 9.10 is no longer the default in GRUB.
Running update-grub doesn't help because it still uses the GRUB from the new version.
With GRUB 2.0 I can't find any safe way to edit.
How can I do that, or how can I change the sequence of choices in GRUB without having to do a full re-install?

(And why was GRUB "upgraded" in the first place?)

---

### Post by wilee-nilee on 2010-12-16
> **ingeva said:**
> A few days ago I installed Ubuntu 10.10 Desktop edition.
The install was OK, but it didn't give me any choice about updating the boot record.
The result, of course, is that my permanent, tested 9.10 is no longer the default in GRUB.
Running update-grub doesn't help because it still uses the GRUB from the new version.
With GRUB 2.0 I can't find any safe way to edit.
How can I do that, or how can I change the sequence of choices in GRUB without having to do a full re-install?

(And why was GRUB "upgraded" in the first place?)

Progress man, progress, there is a program called startup manager in synaptic, software center or in the terminal. It will allow you to set the default booting OS at the grub menu.

---

### Post by ingeva on 2010-12-16
> **wilee-nilee said:**
> Progress man, progress, there is a program called startup manager in synaptic, software center or in the terminal. It will allow you to set the default booting OS at the grub menu.
Thanks!
That's great, but I fail to see the progress here .... :)

---

