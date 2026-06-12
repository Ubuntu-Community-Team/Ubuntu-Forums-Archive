---
title: "Can't boot from hard disk..."
date: 2006-07-17
forum: Desktop Environments
---

### Post by stinkball on 2006-07-17
I need help booting to my ubuntu partition: everything was working fine yesterday, but this morning I turned on my computer and my computer wouldn't boot. I repaired the MBR so i could boot to xp and now i can't boot to ubuntu.  is there a way i can load grub with the windows NT bootloader?  if not how do i install GRUB again?

sorry i'm such a newbie, i just started using ubuntu.

---

### Post by thoolihan on 2006-07-17
Boot using the livecd.  Get into a terminal and mount your disk
something like, and chroot to it and run grub, something like:

mount /dev/hda2 /mnt/ubuntu
chroot /mnt/ubuntu -s /bin/bash
source /home/stinkball/.bashrc
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

reboot and test

-Tim

---

### Post by stinkball on 2006-07-18
sorry thoolihan, that didn't work.  I ended up using super grub disk from here: [http://adrian15.raulete.net/grub/tiki-file_galleries.php](http://adrian15.raulete.net/grub/tiki-file_galleries.php)

and it fixed grub.

---

