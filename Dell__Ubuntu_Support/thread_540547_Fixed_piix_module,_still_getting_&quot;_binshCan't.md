---
title: "Fixed piix module, still getting &quot; /bin/sh:Can't access tty; Job control turned off&quot;"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by IanKoro on 2007-09-01
I'm sure a lot of you are familiar with the issue where you boot into the initramfs prompt getting " /bin/sh: Can't access tty; Job control turned off "... Well, I've gone through the standard fix, adding piix to the modules that are loaded, so I don't have to type "modprobe piix" anymore, I'm able to just type "exit", and everything boots up fine.

But it's still irritating. As I'm sure you understand, I'd like to just boot normally. It seems that most people are able to add piix, update initramfs, and the problem is fixed, but it's still partly there for me... Any ideas?

Oh, forgot to mention, I'm running a Dell Inspiron 1420, and I've managed to get pretty much everything else working.

If you want, I'll attach the output of dmesg or lspci, or anything you think you'll need.

---

