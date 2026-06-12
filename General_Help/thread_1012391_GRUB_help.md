---
title: "GRUB help"
date: 2008-12-15
forum: General Help
---

### Post by miked860 on 2008-12-15
I'm going to be installing Windows XP on another partition after having Ubuntu installed. How could I edit GRUB to include XP after it is installed?

---

### Post by logos34 on 2008-12-15
here you go:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

install and run ntfs-config too

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by eBoxNet on 2008-12-15
You can always boot from your live cd and reinstall grub.
After that you will have dual boot menu.

---

### Post by logos34 on 2008-12-15
miked860,

reinstalling grub by itself will not make it dual-boot--you will still have to manually add the windows entry to menu.lst

---

### Post by eBoxNet on 2008-12-15
miked860 he is right i thought you where re-installing windows.

SORRY my bad !:confused:!!

---

### Post by miked860 on 2008-12-15
Thanks for the help everyone. Doesn't look as hard as I thought it would be.

---

### Post by miked860 on 2008-12-15
> **logos34 said:**
> miked860,

reinstalling grub by itself will not make it dual-boot--you will still have to manually add the windows entry to menu.lst

How will I be able to do that if I won't be able to get into Ubuntu once I install XP. XP will install the windows boot loader so I won't be able to get into ubuntu to edit the menu.lst right?

---

### Post by eBoxNet on 2008-12-15
not so sure but i am thinking that you could reinstall grub from live cd and then boot ubuntu and edit your menu list.

---

### Post by logos34 on 2008-12-15
> **miked860 said:**
> How will I be able to do that if I won't be able to get into Ubuntu once I install XP. XP will install the windows boot loader so I won't be able to get into ubuntu to edit the menu.lst right?

i assumed you knew that.  Like eBoxnet says, you can restore grub from the ubuntu live cd.  See link in my signature.

good luck

---

