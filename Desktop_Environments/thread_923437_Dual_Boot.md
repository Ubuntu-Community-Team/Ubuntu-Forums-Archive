---
title: "Dual Boot"
date: 2008-09-18
forum: Desktop Environments
---

### Post by chrislynch8 on 2008-09-18
HI,

I have a Laptop with XP and I installed Ubuntu onto it as a Dual boot - now I want to remove Ubuntu from it and keep my XP install nad just extended the partition to include the Ubuntu Partition.

How do I remove the Ubuntu installation correctly without correctly XP. I tried to remove Ubuntu before but XP still looked for GRUB to boot and I had to install Ubuntu again to get into XP.

Chris

---

### Post by caljohnsmith on 2008-09-18
If you want to be able to boot into Windows right after you uninstall Ubuntu, you'll have to run "fixmbr" from your Windows Install CD. But if you are going to reinstall Ubuntu to an extended partition, you could just do that and it will reinstall Grub with it.

---

### Post by chrislynch8 on 2008-09-18
Ya I want to completely remove Ubuntu so then I have to run my a XP cd and run mixmbr.

Perfect 
Thanks 
Chris

---

