---
title: "InitNG problems"
date: 2006-03-14
forum: Desktop Environments
---

### Post by kundalinikat on 2006-03-14
The new kernel rewrote my /boot/grub/menu.lst. I installed a newer GRUB... uninstalled it, reinstalled it... had an "error 15 file not found" thing, fixed that somehow (not even sure how, but I was using advice from this lovely forum)... my GRUB menu works now, and it finds and boots the new kernel but then I get this message!

[4294668.177000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by engla on 2006-03-14
Something is inconsistent, confused or we need more information.

initng does nothing with the kernel, except that you have to modify the kernel's command line

So it looks like you need to reinstall grub properly, anyhow. I don't know how to do that, but search for it.

Also -- this error is it with normal boot-up or with initng?

---

### Post by kundalinikat on 2006-03-15
The error message is with InitNG. But I guess the real problematic things are, when (from GRUB) I choose to boot the kernel sans InitNG, my wireless card is no longer detected and my sound and printing don't work.

---

