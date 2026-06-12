---
title: "Grub! :-("
date: 2006-01-05
forum: Desktop Environments
---

### Post by Juzz on 2006-01-05
Why oh why - does grub remove my preferences each and every time a new kernel is installed?

It gets tiresome to have to re-edit the menu.lst every f...... time :mad:

---

### Post by ysse on 2006-01-06
If you just edit the kernel-lines in menu.lst, they **will** get rewritten each time grub is reconfigured to include a new kernel. I didn't read the fine print either, the first few times. Look after ##BEGIN AUTOMAGIC KERNELS LIST.

# kopt: here you set options used for all kernels.

# nonaltoptions: for preferences to the primary entry for each version, and 

# altoptions for options to the recovery mode entries.

Remove the options you don't want, and set the options you want after # kopt, # nonaltoptions and # altoptions. 

Or did you mean that **those** options get overwritten too?

---

### Post by Juzz on 2006-01-23
Yup, those settings get overridden too...

The first boots were fine and all - then when I updated the kernel they were gone.

Also gone is my pretty boot config with the green "OK", so I gotta dig out that howto again ;)

---

