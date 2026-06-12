---
title: "I have problem for boot my labtops"
date: 2008-05-31
forum: Desktop Environments
---

### Post by aurora_consurgens on 2008-05-31
Hello, Everybody

I have problem and I think it's hard for me. This is my problem.

When I boot my laptop I can't start Gnome Display and it shown this message.

kinit : name_to_dev_t(/dev/disk/by-uuid/21f22d29-87a0-494f-ba81-b4164be38b6c)=sda4(8,4)
kinit : trying to resume from /dev/disk/by-uuid/21f22d29-87a0-494f-ba81-b4164be38b6c)=sda4(8,4)
kinit : No resume image, doing normal boot...

And When I enter to Recovery Mode I found 

Starting GNOME Display Manager ..............[Failed]

How can I solve this ploblem?

Thank you

---

### Post by bwhite82 on 2008-05-31
You can boot to CLI in safemode right? If so, at the prompt edit menu.lst and add the noresume kernel option:

> sudo nano /boot/grub/menu.lst

Scroll down to the kernel lines and at the very end add: noresume

Something to try for GDM after you're done editing:

> sudo dpkg-reconfigure gdm

Then:
> 
startx

---

