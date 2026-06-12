---
title: "Removing Grub"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-08
I had XP on my main HDD and Fedora Core 5 on my second, it came with GRUB of course, but now I don't need FC5 and I put Ubuntu as my main OS and uninstalled XP, so I don't need GRUB anymore (at least I don't think? It's not neccessary is it?), how can I remove it and have Ubuntu just boot automatically?

---

### Post by whizbaby on 2006-09-08
Bad idea to remove grub. After a kernel upgrade (or compile-kernel-on-my-own-session), how would you switch back to the old kernel? How would you be able to boot into the rescue system?
So leave it where it is. If you don't want to see it uncomment the *# hiddenmenue* line in /boot/grub/menu.lst . (I think it won't even start without a boot manager in MBR)

---

