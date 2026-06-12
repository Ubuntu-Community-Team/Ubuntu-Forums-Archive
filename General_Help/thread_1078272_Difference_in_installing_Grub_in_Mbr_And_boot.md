---
title: "Difference in installing Grub in Mbr And /boot"
date: 2009-02-23
forum: General Help
---

### Post by deepakbm on 2009-02-23
What is the difference in installing Grub in Mbr And /boot?


how to find where my grub is installed ?

---

### Post by DagMan on 2009-02-23
The MBR is a very small section of the hard drive, so you can't put much there.  The grub info there is enough to store where the rest of the things needed to boot are located... the grub files in /boot/grub, the kernel files in /boot, what partition they are on...
Grub on the drive are the files that are needed to boot, once the MBR knows where they are.  This is typical of how operating systems boot btw.

When you ask where your grub is installed, the answer is that it is in both places, but more importantly is to know if you are wanting to do something, fix something, change something, etc, with grub, and then your question is easier to address.

---

### Post by plucky on 2009-02-23
Learn about Grub [here](http://users.bigpond.net.au/hermanzone/p15.htm#page%20index)

---

