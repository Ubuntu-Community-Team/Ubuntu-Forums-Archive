---
title: "Not GRUB, and not LILO, but..."
date: 2009-04-23
forum: General Help
---

### Post by ansabhailte on 2009-04-23
I was wondering if I can use the boot option dialog at the startup of Backtrack to actually choose between different linux installations? I have a USB flash drive with backtrack and ubuntu installed, and since backtrack is a live cd and has lilo, I cant use grub, and i cant configure lilo. can i just add an option pointing it to another partition?

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw quiet

label ubnentry0
menu label BT4 Beta - Console
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz vga=0x317  ramdisk_size=6666 root=/dev/ram0 rw quiet

label ubnentry1
menu label BT4 Beta - Console no FB
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw quiet

label ubnentry2
menu label Run Memtest utility
kernel /boot/mt86p
append initrd=/ubninit

---

