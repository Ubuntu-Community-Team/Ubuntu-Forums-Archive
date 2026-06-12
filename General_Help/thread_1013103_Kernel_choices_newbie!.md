---
title: "Kernel choices newbie!"
date: 2008-12-16
forum: General Help
---

### Post by Paul666 on 2008-12-16
Sorry if this has been asked before, but just a quick question from a ubuntu newbie, when  booting i have a choice of 2.6.27-7 or 2.6.27-9 kernel to boot from, my question is will the changes i make in one kernel apply to the other? or are they independant.

---

### Post by mali2297 on 2008-12-16
You won't be making changes to the kernel itself. Your personal data, user settings etc are stored in separate files.

The reason for keeping old kernels is that sometimes something might break after a kernel upgrade. In that scenario, you have the option to use the old reliable kernel.

---

### Post by donkyhotay on 2008-12-16
Well, you might *theoretically* make changes to the kernel itself if you compile a specific driver into the kernel or compile your own kernel from source. This is pretty advanced though and not something a casual user is likely do. Even if you did do this it only affects how that particular kernel functions (3d acceleration and stuff) and doesn't change anything with your personal files.

---

