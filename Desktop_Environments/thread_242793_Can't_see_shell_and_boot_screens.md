---
title: "Can't see shell and boot screens"
date: 2006-08-24
forum: Desktop Environments
---

### Post by 0m4r on 2006-08-24
Good Morning to all,
  I'm really new to ubuntu and linux too.
I've yet installed the new Ubuntu Drapper 6.0.6 on my old laptop (It's a Geo Focus 350 - Celeron 650Mhz).

The problem is that I can't read nothing when I start the OS, the LCD screen "goes mad" and I can view something just when GNOME is loaded. The same happen if I want to use a shell (CTRL+ALT+F1, for example): I can't see nothing...

Does anyone could help?

Thanks a lot,
  Omar

---

### Post by Dr.Fix on 2006-08-24
I think it to be a bootsplash issue.

Try editing kernel line in grub removing it:
- Select you kernel in grub
- Press "e"
- Select the "kernel" line
- Press "e"
- Delete "quiet splash etc." until "ro" (excluded, leave it)
- Press enter and "b"

---

### Post by Dr.Fix on 2006-08-24
Probably your graphic card doesn't support FrameBuffer.

Try using a generic vesa framebuffer to solve it or permanently disable bootsplash.

You can have nice fonts (instead of ugly 640x480 ones) just editing
/boot/grub/menu.lst

and replacing "quiet splash" with "vga=0x323" (wich means 1024x768 )

---

### Post by 0m4r on 2006-08-24
it works!
Thank you very much!

---

