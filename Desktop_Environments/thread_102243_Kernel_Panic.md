---
title: "Kernel Panic"
date: 2005-12-11
forum: Desktop Environments
---

### Post by BrianB on 2005-12-11
After recompiling the kernel (from the vanilla sources) I get the error "Kernel Panic-not syncing:VFS: Unable to mount root fs on unknown block (22,3)" I'm pretty sure I've got everything that needs to be statically compiled in done so but I'm a noob so you know...Anybody got any help on this?

---

### Post by haykel on 2005-12-11
Generally this is due to the kernel not finding your drives. The cause is some module not being loaded (ATA/SCSI-driver, ext3-driver, ...). Even if you think you compiled everything you need statically, perhaps you forgot something! The most important things is to have the filesystem module compiled statically and try to compile everything else (don't take many things out) as modules. Then make sure you build the kernel with initrd support (call make-kpkg with the --initrd option) and your initrd image is being loaded (specified in the bootloader configuration).

---

### Post by hod139 on 2005-12-11
Make sure that the root filesystem (assuming ext3) is compiled into the kernel, not loaded as a module.  This will probably fix the error.

---

### Post by BrianB on 2005-12-11
Can the vanilla kernel make use of initrd or does it need a patch?

---

### Post by syroz on 2005-12-14
i 've the same problem to. i've checked all the possible fileSystem in the menuconfig but still kernel panic. any other ideas?

---

