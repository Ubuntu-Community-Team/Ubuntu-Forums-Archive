---
title: "Removing Windows Harddrive - Master Boot Record issue"
date: 2006-09-30
forum: Desktop Environments
---

### Post by godtvisken on 2006-09-30
Hello,

Currently I have on hda my windows XP drive, and on hdb Ubuntu. I would like to remove the windows drive and use it in another box, but I think that the MBR is stored there. I attempted to remove it and when I tried to boot, grub never came up. So then, what must I do? It seems that I should remove the drive, then boot into a CD distro of Ubuntu and put grub on the Ubuntu drive and edit fstab. Is this right? 

Thank you!

---

### Post by DeathOnJuice on 2006-09-30
That should do it for you, as far as I know. However, I'm not quite as knowledgeable about Linux as some people around here, so if you're not comfortable messing around with stuff on my word alone, wait for someone else to respond. I'm pretty sure it should work, though.

---

### Post by godtvisken on 2006-09-30
When I boot from the CD, how do I go about installing grub to the harddrive?

---

### Post by CatKiller on 2006-09-30
> **godtvisken said:**
> When I boot from the CD, how do I go about installing grub to the harddrive?

[How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351&highlight=GRUB+HOWTO")

---

