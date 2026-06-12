---
title: "Debian lenny bootup, dropped to a shell."
date: 2009-04-21
forum: General Help
---

### Post by dragos240 on 2009-04-21
Hi, I just got grub to install on my flash drive, and now it boots into grub flawlessly, and even loads debian lenny without error 17. Although, I've encountered another problem. When debian boots, it drops to a shell. My teacher always said that taking notes is important, I kept this in mind, and wrote down when it seemed to be going kooky:

```

check root =bootarg cat /proc/cmdline or missing modules,
devices : cat /proc/modules is /dev
ALERT! does not exist.
Dropping to a shell!

```

That's what it did. Can I get some seggestions? I think I know something to do with it, I orgonized the /boot directory into 3 sections;

grub
images
kernels

and i left 2 files in the main boot directory. Help?

---

### Post by dragos240 on 2009-04-21
Nevermind. I got it again.....

---

