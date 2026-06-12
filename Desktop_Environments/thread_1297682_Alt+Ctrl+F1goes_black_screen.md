---
title: "Alt+Ctrl+F1goes black screen"
date: 2009-10-22
forum: Desktop Environments
---

### Post by arcull on 2009-10-22
Hi there. I did update my kde 4.3 recently on kununtu 9.04 via```
apt-get install kubuntu-desktop
``` Now I experience some strange behaviour, when pressing key combinations to get to CLI mode from KDE (Alt+Ctrl+F1..F6) I get only black screen, if I press Alt+Ctrl+F7 I can get back to KDE without problem. The same result is when logging to konsole from kdm manager, if I select konsole login instead of kde, it goes black screen, but not always, sometimes it works ok, sometimes not. It looks like random choice. Do you have any idea what could be wrong? Thanks

---

### Post by Zorael on 2009-10-24
That sounds like a framebuffer problem. Did you set any special 'vga=' lines in your grub configuration?

---

### Post by arcull on 2009-10-24
Thanks Zorael. The only thing I changed in /boot/grub/menu.lst was the to add one start up kernel parameter (acpi_oss) ```
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0e8d15ab-e7f2-45c5-bba8-a5c080f80128 ro quiet splash acpi_osi=Linux 
```, but this didn't cause any problems until my kde update, so there must be something else. Any other idea maybe?

---

### Post by Zorael on 2009-10-24
I don't think it's caused by KDE, but either caused by your X drivers (Nvidia, Intel, ATI, whatnot) not properly "releasing" the screen so that the framebuffer can display the console, or the correct framebuffer module not being loaded.

If you start in recovery mode, do you see the console there?

This used to happen in kernels a few releases back ([info](http://www.savvyadmin.com/console-framebuffer-in-ubuntu)), which needed the modules to be explicitly loaded. As per [comment #43](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/43) in [launchpad bug #129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910);
> on my virtual pc installation i fixed the problem with the following steps:

1. sudo vi /etc/initramfs-tools/modules and add fbcon and vesafb

so my /etc/initramfs-tools/modules looks like:

fbcon
vesafb

2. sudo update-initramfs -u

3. sudo vi /etc/modprobe.d/blacklist-framebuffer

change the line "blacklist vesafb" to "# blacklist vesafb"

4. reboot and everything is fine

HTH
MOM
Replace vi with nano to get a more sensible interface. Or use a graphical editor. No guarantees though, keep a live CD around just in case you need to emergency-revert the change.

---

### Post by arcull on 2009-10-24
Thanks _Zorael_, I'll give it a try :)

---

