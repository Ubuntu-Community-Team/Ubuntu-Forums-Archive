---
title: "error: no such partition grub rescue&gt;"
date: 2012-07-19
forum: Delhi Team
---

### Post by pradhan on 2012-07-19
I had dual boot with linux and win7. I tried to format c drive to install win7 but I ended up in a black screen giving me:

"
error: no such partition.
Entering rescue mode...
grub rescue>"

I tried few commands and few steps but they didn't help me... I don't have DVD drive and USB is not working... Please get me out of this black screen...

information:

grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos2) (hd0.msdos1)

Please help...

---

### Post by oldfred on 2012-07-19
Welcome to the forums.

It would be best to have a LiveCD or USB to boot from.

You may be able to manually boot.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command. (hd0,msdos5) is the same as (hd0,5)
configfile (hd0,1)/boot/grub/grub.cfg

#If above does not work try this, again the hdX,Y and sdaY needs to be the drive & partition of your install:
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

