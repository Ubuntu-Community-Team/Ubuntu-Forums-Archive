---
title: "Error 21 at boot"
date: 2009-06-05
forum: General Help
---

### Post by jhouse59 on 2009-06-05
Just installed Ubuntu Studio 9.04. I'm dual booting with Windows XP. When I installed Ubuntu. I just had 2 hard drives connected (in case I made a mistake). I've got 2 PCI cards. One is for extra IDE and the other is SATA drives. After the installation I connected the hard drives to the cards. But, when I booted I got this error message: "Grub loading, Please wait... ERROR 21". I tried unhooking each hard drive to see if it was a certain card. I couldn't get my computer to boot into Ubuntu till each one was disconnected.
Can someone tell me what I need to do to fix this? I've hooked the the drives up and booted with a live cd. Just to copy files I needed.

---

### Post by lindsay7 on 2009-06-05
You need to change your bios so that I boots of the correct drive. Figure out which drive has the os systems on it and boot that one first. You may still need to make a change in the grub menu but do this first.

---

### Post by jhouse59 on 2009-06-07
> **lindsay7 said:**
> You need to change your bios so that I boots of the correct drive. Figure out which drive has the os systems on it and boot that one first. You may still need to make a change in the grub menu but do this first.

Thanks lindsay7. I'd forgot about changing the BIOs boot order.

---

