---
title: "Multiple entires on grub"
date: 2005-12-14
forum: Desktop Environments
---

### Post by montes.c on 2005-12-14
How do I remove the entries of kernels on grub that I don't use? Even if I do edit the grub menu, aren't the old kernels still there? How do I remove this?

---

### Post by hollowhead on 2005-12-14
my understanding is this is not advisable since it can lead to problems if you upgrade kernel.  I could be wrong though.  I would read the grub site instrunctions first.

---

### Post by MartinG on 2005-12-14
If you're happy with the new kernel it's quite safe to remove the old one via synaptic, and grub will update automatically.

---

### Post by montes.c on 2005-12-14
[QUOTE=MartinG]If you're happy with the new kernel it's quite safe to remove the old one via synaptic, and grub will update automatically.[/QUOTE]

There is nothing in synaptic that shows that

---

### Post by linkunderscore on 2005-12-14
I just commented the extra entries out from the grub menu. That works fine for me....I wouldn't mind removing some kernels I don't need as long as I can be assured its not going to screw up further upgrades.

---

### Post by MartinG on 2005-12-14
[QUOTE=montes.c]There is nothing in synaptic that shows that[/QUOTE]

Not quite sure what you mean.  If you search synaptic for "linux" you will get all the kernel info, and can select for removal all the packages relating to the kernel you want to remove.  Just make quite sure that nothing is marked for removal relating to the current kernel!

It's worked for me three times (at least), and grub has always been updated  by synaptic. (I suppose if you are using home-built kernels this may not apply.)  This won't affect future upgrades, as the kernel "set" of packages belong together.  Of course, if you have any custom-built modules (I have three, for VMWare, for a webcam and for the new NVidia driver) they have to be rebuilt after each upgrade, but keeping old kernels won't help as the modules are very much kernel-version specific.

You can modify grub by commenting out the unwanted entries in /boot/grub/menu.lst, but when you upgrade the automagic stuff will re-insert the old menu entries if the old kernel is still around.

---

