---
title: "Black screen upon boot"
date: 2010-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Graeme2804 on 2010-07-06
Hi,

My Dell Inspiron 1525 has a completely black screen.  When I start it up, the dell screen flashes for a split second and then goes black whilst it boots up.

The reason I'm creating a new thread is because all the others seem to be able to get a live cd or usb to work, I can't, I don't even get to that stage of the boot.

I can get in via ssh though, because it still goes through the boot process even though I cannot see it.

I've tried doing apt-get update+upgrade to see if there was some corrupted packages but nothing has worked yet.

I'm glad I've got in via ssh as I've managed to backup the files, but I really need this laptop working again asap.  I suspect it's not a hardware issue due to the Dell startup screen flashing at the start.

---

### Post by Graeme2804 on 2010-07-06
bump

---

### Post by bcbc on 2010-07-06
What video card do you have?

If it's nvidia you could try adding nomodeset to the boot options. Since you can ssh you can just edit /etc/default/grub and add to the GRUB_CMDLINE_LINUX_DEFAULT option so it shows ="quiet splash nomodeset".
Then update-grub to get it into the menu.

If you want to do it on the fly, hold down the SHIFT key to get the grub menu to show (assuming grub2), press 'e' on the first entry and add nomodeset after quiet splash, then CTRL+X to boot.

If it's not an nvidia there are some other things you can try

---

