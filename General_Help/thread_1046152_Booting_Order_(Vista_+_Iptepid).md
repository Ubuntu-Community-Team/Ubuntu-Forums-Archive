---
title: "Booting Order (Vista + Iptepid)"
date: 2009-01-21
forum: General Help
---

### Post by GrimmReaperVI on 2009-01-21
I just installed Intepid on my new PC (hooray!) but one thing that's been bugging me is that there are 2 Vista boot options which are identical and ubuntu is first. Like:

Linux Intepid 8.10 Kernel
Linux Intepid 8.10 Kernel (recovery)
memtest (I forgot to remove that)
Other Operating Systems:
Vista Langhorn
Vista Langhorn

I want something like:

Vista Langhorn
Linux Intepid 8.10 Kernel
Linux Intepid 8.10 Kernel (recovery)
Other Operating Systems:

I want to remove "Other OSs" but if I can't I'd have that at the bottom :D

I have startup manager, but I'm not sure how to change the order :???:

Vista boots first always
Also, can I rename them?

---

### Post by jespdj on 2009-01-21
Edit /boot/grub/menu.lst:
```
gksu gedit /boot/grub/menu.lst
```
Note: Be CAREFUL with this, if you put something wrong in that file, GRUB might be unable to boot your system.

---

### Post by GrimmReaperVI on 2009-01-21
*Gulps* A little help here, anyone?

---

