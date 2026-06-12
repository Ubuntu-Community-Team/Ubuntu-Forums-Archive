---
title: "Grub, Error 17"
date: 2008-12-06
forum: General Help
---

### Post by arislaracarrion on 2008-12-06
ive been looking around for a few hours now and i cant find a solution for me, ive tried all the commands to re install grub in terminal but i get error 15: file not found.

i was dual booting XP and Ubuntu(latest version) and when i went into my XP i went to norton partition magic, i clicked on format partition( the ubuntu one) and it asked me to reboot. i did and i got error 17. I cant even get into my xp partition anymore im using a live CD right now. 

any more info u need to know please tell me
help!

---

### Post by eBoxNet on 2008-12-06
if you need to access your windows installation try to fix windows mbr 

check this link : [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

---

### Post by arislaracarrion on 2008-12-06
"Microsoft is exceptionally vague regarding the conditions under which fixmbr can cause problems although they are clear about the consequences (losing all data on the hard drive), so use this at your own risk."

is there any other solution to this

---

### Post by arislaracarrion on 2008-12-06
help me out please, will i have to use that fix that above post gave me? or can i fix this another way

---

### Post by Sjeti on 2008-12-06
If you want to manage your OS's with grub:
You should probably get supergrub disk.

Burn it to a live CD and run it.

Run it with help, get it to fix your GNU/linux partition and you should be fine from there.

Once you get grub working you can edit your XP setup to boot properly through grub.  It depends on your setup and what grub sees as your harddrives how you fix it.


I wouldn't know how to help you if you wanted to use windows to boot.

---

### Post by MarblePanther on 2008-12-06
i second supergrubdisk, it is a lifesaver

just burn it to a cd and keep it around--it will come in handy

---

### Post by caljohnsmith on 2008-12-06
From my experience, there is nothing dangerous about running that "fixmbr" from the Windows Install CD if you want to install a Windows MBR. If you want, you can instead do the following command from your Live CD, and it will install a Windows equivalent MBR:
```
sudo lilo -M  /dev/sda mbr
```
Make sure to change "sda" if your drive is different. Either "fixmbr" or the above command should yield the same results.

---

### Post by arislaracarrion on 2008-12-06
```
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
```





thats what i got when i typed ```
sudo lilo -M /dev/sda mdr
```

---

