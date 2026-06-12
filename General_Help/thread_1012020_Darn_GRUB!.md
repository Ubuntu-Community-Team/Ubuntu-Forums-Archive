---
title: "Darn GRUB!"
date: 2008-12-15
forum: General Help
---

### Post by bestseclub on 2008-12-15
So i had XP/Ubuntu dualboot with GRUB.I used Norton PartitionMagic and deleted my Ubuntu partition(its what I want).
After rebooting,Windows wouldnt start!!!The GRUB gave an error and i couldnt do anythin!
I put Ubuntu Live CD in my PC and started with it.I installed the no GUI version or whatever its called!
No when i rebooted,i finally got GRUB to start,but would you look at this!:XP WOULDNT START BECAUSE IT HAD A MISSING DLL!!!I dont have the XP CD anymore!I cant reinstall it.I have important files in my XP ntfs Partition!
Please tell me what to do.I cant believe that grub is so stupid that in removed a system file from my XP partition.
Please tell me theres an easy way to solve this!!!!!!

---

### Post by NSAJEFF on 2008-12-15
If it's XP you want you could try a recovery with the XP disk. It should fix boot record and allow for clean startups of just XP.

---

### Post by Slim Odds on 2008-12-15
> **bestseclub said:**
> So i had XP/Ubuntu dualboot with GRUB.I used Norton PartitionMagic and deleted my Ubuntu partition(its what I want).
After rebooting,Windows wouldnt start!!!The GRUB gave an error and i couldnt do anythin!
I put Ubuntu Live CD in my PC and started with it.I installed the no GUI version or whatever its called!
No when i rebooted,i finally got GRUB to start,but would you look at this!:XP WOULDNT START BECAUSE IT HAD A MISSING DLL!!!I dont have the XP CD anymore!I cant reinstall it.I have important files in my XP ntfs Partition!
Please tell me what to do.I cant believe that grub is so stupid that in removed a system file from my XP partition.
Please tell me theres an easy way to solve this!!!!!!

First, GRUB didn't do anything wrong! You pulled the rug out from under its feet. GRUB did not and will not mess with your DLL's.

GRUB needs to load its configuration file (menu.lst), which you deleted.

What you should do is boot from the XP CD (which you should have) and fix the MBR.

---

### Post by bestseclub on 2008-12-15
Wheres is Grub located?
Cant i just remove it and make XP start by its own?

---

### Post by NSAJEFF on 2008-12-15
> **bestseclub said:**
> Wheres is Grub located?
Cant i just remove it and make XP start by its own?


It doesn't matter where GRUB is located. Simply insert your XP disc and choose the option to recover your system. Also, you broke GRUB. GRUB did not break your system.

---

### Post by bestseclub on 2008-12-15
So how was i supposed to remove Linux?
If it was in the same partition as Linux,it would just be deleted and i could start Windows,as before,when i didnt have Linux partition.
I dont have the XP CD.There isnt a way to remove grub?

---

### Post by logos34 on 2008-12-15
> **bestseclub said:**
> So how was i supposed to remove Linux?
If it was in the same partition as Linux,it would just be deleted and i could start Windows,as before,when i didnt have Linux partition.
I dont have the XP CD.There isnt a way to remove grub?

there's two parts to grub--the tiny stage1/1.5 file on the MBR and the menu.lst on / -- when you boot, grub stage1 looks for the latter on the ubuntu root partition.  You just need to overwrite the mbr with the windows bootloader to get rid of stage1. 

You can use Super Grub Disk (see link my signature) to restore xp loader if you don't have the xp install cd

---

### Post by bestseclub on 2008-12-15
Do i need to reinstall the ubuntu for that?

---

### Post by logos34 on 2008-12-15
no, just dl SGD, burn it to cd and boot it

---

### Post by bestseclub on 2008-12-15
Logos,you just saved me a lot of hours.Thank you.

---

