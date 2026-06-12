---
title: "Splashy Error"
date: 2008-05-28
forum: Desktop Environments
---

### Post by dushkal on 2008-05-28
Hi,

After yesterday's kernel update, Splashy has stopped working.
During the boot, I'm getting following message:

Splashy ERROR: Couldn't splashy_start_splashy(). Error -2

The same message can be seen if I try to test splashy using splashy test

The steps taken so far:
- re-installed splashy
- added the entry vga=791 in /boot/grub/menu.lst 
- renamed udev in /etc/rcS.d/ to start before splashy

but the error persists and I can not start splashy at all.

Any help is appreciated

Cheers,
Dushkal

---

### Post by a0t on 2008-10-04
Try this 
[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)
it worked for me
Actually I only added vga=792 to the kernel line in /boot/grub/menu.lst
Good luck.

---

