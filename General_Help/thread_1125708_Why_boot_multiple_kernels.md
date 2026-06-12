---
title: "Why boot multiple kernels?"
date: 2009-04-14
forum: General Help
---

### Post by camper365 on 2009-04-14
I know that the multiple kernels appear in GRUB after a system update sometimes, but why would you need to boot an old kernel?

---

### Post by James_Lochhead on 2009-04-14
You don't. After a kernel update type sudo apt-get autoremove to remove the old kernels. The entries for the offending kernels can then be removed from /boot/grub/menu.lst.

---

### Post by antikristian on 2009-04-14
I think it's there incase something goes incradably wrong.

You can also use the "computer janitor" to remove them

---

### Post by mb_webguy on 2009-04-14
A kernel update may occasionally break a system.  It's rare, but it happens.  If this happens, you have the ability to boot into an older kernel that works for your system.

You can edit the GRUB menu to limit the number of kernels listed, and you can remove old kernels using Synaptic (though the latter should be done with great caution).

---

### Post by EnglishSparrow on 2009-04-14
Because newer kernels might not always work. For instance, the newest kernel to work with my sound until recently was 2.6.24-18.

---

### Post by juancarlospaco on 2009-04-14
[I]Because you can!
Try to Boot Windows 2000 Kernel on Vista.[/I]

Use **Computer Janitor**.

---

