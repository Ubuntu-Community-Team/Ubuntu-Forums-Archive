---
title: "question about my kernels"
date: 2006-09-20
forum: Desktop Environments
---

### Post by sal on 2006-09-20
i have the default i386 kernel and the generic kernel install. my understanding of it is that the generic kernel is the New i586 kernel.
yet on boot my system defaults to the i386 kernel. i have to manually tell grub every time to load the generic kernel how can i make this happen by default where it loads the generic kernel instead of the i386.

TIA

---

### Post by bulldog on 2006-09-20
Just comment # the kernels you don't want to boot.

Or alter this line in your menu.lst

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#

---

