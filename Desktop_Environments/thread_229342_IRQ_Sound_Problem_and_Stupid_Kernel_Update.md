---
title: "IRQ Sound Problem and Stupid Kernel Update"
date: 2006-08-04
forum: Desktop Environments
---

### Post by brownrl on 2006-08-04
Hip Hoy,

Sorry to nag but I had my sound card working perfectly after I discovered that I had an issue with IRQs.

I had to add pnp=noirq or something simular to the grub menu.

However, the wonderful ubuntu updater updated my kernel and thus killed the changes that I made.

Unfortunately I can't find the topic or article that told me how to do it. Does anyone know?

It was something like: yadayada=noirq and that solved it.

Thanks a ton to anyone,
Rob

---

### Post by tuxinvader on 2006-08-04
I think what you are after is acpi=noirq

If you edit /boot/grub/menu.lst on line 85 you will have:
# defoptions=quiet splash

change it to
# defoptions=quiet splash acpi=noirq

---

