---
title: "GRUB boot loader"
date: 2006-08-09
forum: Desktop Environments
---

### Post by TheEmb3rEgg on 2006-08-09
I recently set up a dual boot with Ubuntu and Windows. When I boot up my computer it automatically boots into Windows. To boot into Ubuntu, I have to go into the boot options, and boot from my other hard drive. From there it takes me to the GRUB boot loader. Is there any way that I can make it so it automatically loads up the GRUB Boot loader?

---

### Post by zxee on 2006-08-10
When you're booted into ubuntu try > sudo grub-install (in a terminal) and select your primary drive usually that's hd0

---

### Post by Hokputooy on 2006-08-10
Try going in to your BIOS and putting your Ubuntu dirve as primary.

---

