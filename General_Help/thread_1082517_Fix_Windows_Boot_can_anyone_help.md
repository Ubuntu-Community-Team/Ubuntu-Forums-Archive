---
title: "Fix Windows Boot can anyone help?"
date: 2009-02-27
forum: General Help
---

### Post by NightwishFan on 2009-02-27
Hi, and thanks for any help.

I installed Ubuntu dual boot with Windows Xp, and Xp gave me a disk error when I had grub try to load it. The data on Windows is fine though.

I am going to download super grub disk, delete Ubuntu and fix windows MBR. I am pretty sure that would work. My goal is to get Windows to work not Ubuntu. Any help?

---

### Post by avrilrox on 2009-02-27
> **NightwishFan said:**
> Hi, and thanks for any help.

I installed Ubuntu dual boot with Windows Xp, and Xp gave me a disk error when I had grub try to load it. The data on Windows is fine though.

I am going to download super grub disk, delete Ubuntu and fix windows MBR. I am pretty sure that would work. My goal is to get Windows to work not Ubuntu. Any help?

If you want to get rid of Ubuntu, use a Windows Cd and "repair" the MBR (Master Boot Record).

I'd suggest editing the menu.lst file. Are you using Grub, right? You can edit the partitions to load the OS from.

---

### Post by Scotty Bones on 2009-02-27
Boot with the win install disk. As it begins to boot you will see a message that says "Press R to enter recovery mode".  This will take you to the recovery console (it looks just like the old DOS screen).  The commands you will want to enter at the prompt are:
fixmbr
fixboot
exit

That should do it for you.

---

### Post by steveneddy on 2009-02-27
> **scotty bones said:**
> boot with the win install disk. As it begins to boot you will see a message that says "press r to enter recovery mode".  This will take you to the recovery console (it looks just like the old dos screen).  The commands you will want to enter at the prompt are:
Fixmbr
fixboot
exit

that should do it for you.

+1

---

