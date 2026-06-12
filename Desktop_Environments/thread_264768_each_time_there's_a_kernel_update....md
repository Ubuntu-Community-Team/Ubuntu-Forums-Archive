---
title: "each time there's a kernel update..."
date: 2006-09-25
forum: Desktop Environments
---

### Post by sha_man on 2006-09-25
...it messes my grub configuration and removes the windows entry there. Fortunately i have a backup of the Grub config, but to update everything manually (add the windows entry remove other etc...) each time the kernel is upgraded is kind of annoying... What can I do to make the process simpler (so that kernel-update does NOT remove the windows entry)?

---

### Post by MrHorus on 2006-09-25
> **sha_man said:**
> ...it messes my grub configuration and removes the windows entry there. Fortunately i have a backup of the Grub config, but to update everything manually (add the windows entry remove other etc...) each time the kernel is upgraded is kind of annoying... What can I do to make the process simpler (so that kernel-update does NOT remove the windows entry)?

It never does this for me...

Anyone else?

---

### Post by anaconda on 2006-09-25
It sounds like you have your windows entry between these lines in your /boot/grub/menu.lst -file.
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```

```
...
...
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Every time kernel is updated all lines between those 2 lines are redone (=changed) automatically.

Just move your windows entry to be after the "### END DEBIAN.." line of before "### BEGIN AUTOMATIC..." line. Then it will be left alone in kernel update.

---

