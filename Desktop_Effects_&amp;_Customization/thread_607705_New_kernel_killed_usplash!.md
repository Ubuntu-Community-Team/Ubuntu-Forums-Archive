---
title: "New kernel killed usplash!"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by Alexis Phoenix on 2007-11-09
Hello nice people :)
I have Feisty installed on a Dell Inspiron 1501 Turion 64 x2 laptop.
I built a custom 2.6.22-6 kernel for it and all seems happy with that.
Trouble is, when I boot into the new kernel, there is no usplash to hide all the boot messages!  I was so looking forward to making a custom usplash screen too :(
There is nothing wrong with usplash itself - booting into the ubuntu supplied kernel (2.6.16-generic) it still comes up as usual.
I believe I need to make an initrd - but when I tried that I got the normal bios bug and pci error messages but nothing else happened.  Initrd seems like dark magic to me, and there doesn't seem to be a reasonably up to date and digestible how-to (someone prove me wrong now!) - can anyone help me do the necessary adjustments to load the stuff usplash needs?

---

### Post by tehet on 2007-11-09
Hi,
Look at /boot/grub/menu.lst
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=49b0c728-7ef4-41e1-925f-bc1880e5d6c5 ro **quiet splash**
```
Add the bold bit to your custom kernel and I think you'll be set. Also I don't think initrd has to do with it, but then again, a flaky BIOS can cause wierd behavior (edit: meaning that initrd can solve some problems with some BIOSes).

---

### Post by Alexis Phoenix on 2007-11-09
Hmm, wish it was that straightforward!
I already have these in my menu.lst.  Thanks anyway!

Alexis

---

