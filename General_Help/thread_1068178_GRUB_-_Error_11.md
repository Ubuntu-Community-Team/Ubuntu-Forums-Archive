---
title: "GRUB - Error 11?"
date: 2009-02-12
forum: General Help
---

### Post by tourist on 2009-02-12
I tried editing GRUB with QGRUBeditor so I could get Windows as the default operating system on startup, and I'm not exactly sure what I did, but I now can't get Ubuntu to load at all. When choosing any of the Ubuntu options at startup, I'm getting an "Error 11: Unrecognized Device String". I've tried using a Super GRUB CD in order to restore GRUB but no luck, and I can't even get to Ubuntu without a Live CD.

Any ideas?

---

### Post by mikewhatever on 2009-02-12
Posting the /boot/grub/menu.lst would be a good way to start.

---

### Post by tourist on 2009-02-12
Here it is:
> default 4
timeout 10

title Ubuntu 8.10, kernel 2.6.27-9-generic
root 
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=a3dd9b01-05ed-493a-a9ef-8759856ba24e ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=a3dd9b01-05ed-493a-a9ef-8759856ba24e ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, memtest86+
root 
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

---

### Post by mikewhatever on 2009-02-12
It says 'root' under every title line, I think it's redundant.

---

### Post by tourist on 2009-02-12
Solved it. Found a backup QGRUBeditor apparently made of my old menu.lst file, so I just switched out the new for the old file and added a "default 4" at the top.

Thanks for your help.

---

