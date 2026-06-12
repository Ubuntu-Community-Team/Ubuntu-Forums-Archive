---
title: "Deleting Windows partition"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Jordan Meeter on 2006-10-07
Hey, I've moved all of my personal files over to Ubuntu and I would like to *delete* the Windows partition and make it so when I turn on my computer, it boots directly to Ubuntu. Can someone walk me through this please?

Thank you,
Jordan

---

### Post by CatKiller on 2006-10-07
Were you using the Windows bootloader before, or GRUB? If you were using GRUB, you just need to change the /boot/grub/menu.lst to remove mentions of Windows. If it was the Windows bootloader, you'll need to install GRUB to the Master Boot Record. There's a "HOWTO install GRUB" somewhere on this forum.

I thought you were going to reinstall Ubuntu anyway? I'm off to bed.

---

### Post by BitTorrentBuddha on 2006-10-07
If you're already using grub to boot then you're in luck and all you have to do is delete the windows entry from your menu.lst and delete the partition by booting into a live disc and deleting it in gparted (probably changing the size(s) of one or multiple other partitions.) If you're not using grub I believe you'll have to play around with things such as changing the MBR.

---

### Post by Jordan Meeter on 2006-10-07
**CatKiller:** I was going to just reinstall Ubuntu, but then I realized that I have 15BG of MP3s that I can't backup anywhere. :p

I'm using GRUB, so I suppose I'll just go ahead and do what you guys said.

Thanks again.

---

