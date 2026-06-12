---
title: "grub messed up...can't pick alternate boot"
date: 2006-08-28
forum: Desktop Environments
---

### Post by plasmafusion on 2006-08-28
hey all :)
i use dapper and recently upgraded my kernel to 2.6.17.7 (to try and get my asus notebook's built in sd card reader to work...it still doesn't) using [this]("http://www.ubuntuforums.org/showthread.php?t=217657&highlight=upgrade+kernel") thread.
the kernel was updated properly with no errors although as i've said my asus a4l's card reader still doesn't function (anyone got any ideas on this?).

on rebooting the grub loader appears as per usual but i can't select any of the alternate boots like i could before (3 ubuntu kernels and xp home) it just boots the latest kernel i installed.

this is very frustrating as i was trying to get my card reader to work as it was the only remaining reason i had to boot into xp...and now i can't even do that to get my camera's images from my sd card.

any help getting my grub boot options back would be great...any help getting my built-in card reader to work would be fantastic also :)

thanks in advance

---

### Post by janbockaert on 2006-08-28
maybe this guide will help?

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_Windows_entry_into_GRUB_menu)

if you open /boot/grub/menu.lst you may be able to find more information on why you can't boot windows. There should be a lot of #comment in the list explaning what the settings mean.

good luck

---

### Post by plasmafusion on 2006-08-28
thanks for the pointers janbockaert.
turns out that the grub countdown timer was set to zero so it booted the default kernel straight away.
still can't get my bl**dy memory card reader to work :(

---

### Post by janbockaert on 2006-08-28
can't help you with your memorycard. Mine (in a dell 9400) works, but i know that is an exception. Call asus and tell them their linux-support s*cks :wink:

---

### Post by plasmafusion on 2006-08-28
heh...yeah many things about this asus of mine suck but i paid a great price for it so shouldn't grumble...
take it easy :)

---

