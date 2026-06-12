---
title: "How do I start Ubuntu 8.04 directly into terminal?"
date: 2009-02-22
forum: General Help
---

### Post by helstreak on 2009-02-22
Thanks for the help :)

---

### Post by mb_webguy on 2009-02-22
1) Open the GRUB menu for editing with "gksu gedit /boot/grub/menu.lst".

2) Find your main Ubuntu entry, which should look something like this.```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

3) Copy that, then paste it either above or below the Automagic Kernels List section.  Add the word "text" to the end of the kernel line, and change the title to whatever you want to distinguish it from the normal entry.  You should end up with something like this.```
title		Ubuntu 8.10, kernel 2.6.27-11-generic **(console)**
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro quiet splash **text**
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

4) Save and exit.

The next time you reboot, you will have that option available in the GRUB menu.  Select it, and it will boot directly to a console login.

---

