---
title: "GRUB uninstallation"
date: 2009-06-10
forum: General Help
---

### Post by samurai_47 on 2009-06-10
i recently was testing out hackintosh on my PC, i had windows on one drive, OS X on another and another drive set for storage, something went wrong when i installed 9.04. somehow the installation failed, even though it said it was successful, my windows partition was nuked and couldn't boot and ubuntu wouldn't do anything....

so long story short i got my computer back in order(somewhat), windows and OS X running, but i have to use the F8->Boot menu to select the hdd to boot from because GRUB is still hanging around somewhere and wont go away. by the way i did reinstall/reformat and put windows back on the same drive. so im thinking GRUB is stuck on the storage drive and i dont know how to get rid of it. 

so i someone has a answer to this i would be very happy

i hope i made that clear enough too

---

### Post by samurai_47 on 2009-06-10
bumping

---

### Post by ethoxyethaan on 2009-06-10
Don't bump a tread unless its inactive for 12 hours.

sudo grub
find /boot/grub/stage1

this will return the location of the grub if you want to know where its located.


to remove the grub for windows and use the windows MBR type (as administrator on windows): 

FIXBOOT C:
FIXMBR
BOOTCFG /rebuild 

i have no idea how to Boot into your Mac OS tough.

---

### Post by samurai_47 on 2009-06-10
mmm no mac os x is perfectly fine, its the windows drives that are giving me crap, but srry for the rule violation, i didnt know about that, thanks for the heads up.

but if grub turns up on my storage drive, would the fixMBR command work for that, even though windows is not installed there?

---

