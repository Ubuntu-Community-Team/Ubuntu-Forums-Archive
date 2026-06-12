---
title: "Everything was fine and then......."
date: 2005-05-16
forum: Desktop Environments
---

### Post by NoTiG on 2005-05-16
Something happened! . im not sure what...... I had a perfectly working 32 bit linux distro on my 3rd partition (hda3) ... and i shutdown... to play with the second partition and installed 64 bit ubuntu..... but anyways... when I now try to boot up the 32 bit distro on my 3rd partition it says:

art-stop-daemon unable to start /sbin/klogd : permission denied [FAIL]

Starting Gnome Display manager [FAIL]

Starting deferred execution scheduler [FAIL]

Those are the only 3 that fail... everything else works. I would boot into rescue mode but... what do i rescue?!? WHen i try to boot up it fails to boot up X and sends me to command line login. when i try to login ... it wont let me log in either . 

help!

---

### Post by az on 2005-05-16
Installing on another partition should not affect the installation on another partition.  Does grub give it a funky parameter, or something?

Compare the /boot/grub/menu.lst in both partitions.  The last one to be installed is the one that is running.  I really do not think that could be it, though....

---

### Post by NoTiG on 2005-05-16
[QUOTE=azz]Installing on another partition should not affect the installation on another partition.  Does grub give it a funky parameter, or something?

Compare the /boot/grub/menu.lst in both partitions.  The last one to be installed is the one that is running.  I really do not think that could be it, though....[/QUOTE] 

I tried cp'ing the boot menu from hda3 to hda2... everything still boots but hda3 still does not load properly.

I know the easy way out is just to reinstall... but i would rather know what happened :(

The only other thing i might mention is that while on hda2 playing with the new 64 bit distro... i did mount the hda3 and browsed some directories. Maybe that has something to do with it i dont know :(.

---

