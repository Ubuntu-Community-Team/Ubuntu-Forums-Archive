---
title: "Fedora To Ubuntu"
date: 2007-02-01
forum: Fedora/RedHat and derivatives
---

### Post by AgentSmith15 on 2007-02-01
Hi I installed Fedora on my laptop and I was wondering if there is a safe way to switch to Ubuntu without harming Windows XP? Last time I switched I deleted the Linux partion and it messed with the boot loader thus making it difficult to boot. Also Fedora thinks my other bootable partion is the system restore drive 0,1 when my XP partion is on 0,0. Any help will be gladly appreciated.

---

### Post by Jagot on 2007-02-01
I would go for deleting the Fedora partition during the partitioning phase of the Ubuntu install, then just allow Ubuntu to use the free space to install itself in.  Ubuntu will overwrite your bootloader with it's own GRUB, and Ubuntu happens to be much better at detecting Windows properly than Fedora is.

---

### Post by AgentSmith15 on 2007-02-01
I agree, Ubuntu seems better at detecting Windoze. Unfortunately Ubuntu isn’t too good with compiling packages, and I hate to wait for stuff to be released as a deb package.

Thank you

---

