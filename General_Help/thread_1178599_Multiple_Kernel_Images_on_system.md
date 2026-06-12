---
title: "Multiple Kernel Images on system"
date: 2009-06-04
forum: General Help
---

### Post by dh4evr on 2009-06-04
How many Linux kernel images do I really need?

When I type:
$ dpkg --list | grep linux-image

I get:
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-21-generic              2.6.24-21.43                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-22-generic              2.6.24-22.45                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-23-generic              2.6.24-23.52                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-24-generic              2.6.24-24.53                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.24.26                       Generic Linux kernel image

Which ones do I need and how do I get rid of the ones not needed, if any?

Currently running Ubuntu 8.04.2 (Hardy Heron)

Thanks in advance...
dh4evr

---

### Post by ajgreeny on 2009-06-04
You can get rid of any older ones you want to in synaptic.  I always keep two versions just in case anything goers wrong with the one I boot by default.

If I were you I would uninstall:-
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-21-generic              2.6.24-21.43                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-22-generic              2.6.24-22.45                       Linux kernel image for version 2.6.24 on x86

---

