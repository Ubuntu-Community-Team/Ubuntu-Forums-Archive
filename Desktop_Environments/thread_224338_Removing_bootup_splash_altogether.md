---
title: "Removing bootup splash altogether?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Roque on 2006-07-27
Is there a way to remove the bootup splash screen? (the one that says "ubuntu" in orangeish letters with brown text scrolling below that appears immediately after computer switch on) 

I mean not to change it with another one, but to completely discard it. I prefer the old school verbose white text scroll since it gives much more (and direct) feedback.

Many thanks in advance.

---

### Post by rocketman768 on 2006-07-27
Edit your /boot/grub/menu.lst file or whatever config file your bootloader uses. Under the entry for the kernel you boot, remove the "splash" option and replace it with "nosplash".

---

### Post by Roque on 2006-07-27
Worked great. Many thanks!

---

### Post by rocketman768 on 2006-07-27
Hehe. Thanks to you also!

---

### Post by Dinerty on 2006-07-30
Worked a treat thanks :)

---

### Post by kurup on 2006-08-08
Hi..is there a way to decrease the font size of the verbose? ..like the one you see during the gentoo installtion startup

---

### Post by feroxjb on 2006-10-04
I also would like to know how to change the font size of the verbose.. anybody?

---

