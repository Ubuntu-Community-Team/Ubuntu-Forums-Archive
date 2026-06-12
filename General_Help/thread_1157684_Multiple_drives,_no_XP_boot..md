---
title: "Multiple drives, no XP boot."
date: 2009-05-13
forum: General Help
---

### Post by Vipersfate on 2009-05-13
I currently have 3 hard drives in my system. Ubuntu boots up fine, and works flawlessly for me. Some problem though.

I currently have Windows XP set up on a dual 80GB HD RAID 0 Array. 

My RAID controller lists both drives in the array and operating normal, but I cannot boot XP. the menu.lst does not list my Windows XP Array. 

I honestly have no idea how to repair this. Grub does not give me the option to boot to the RAID array, as well as if I select the RAID as the boot device, it fails to load GRUB. Please help! Thanks!

---

### Post by Williamthecg on 2009-05-13
i have had a prob like this  fixing it is easy if you hae a win xp repair, install, or upgrade disk insert disk (with bios set to cd 1st) then go to repair and login then type  fixboot and press enter then Type fixmbr and press enter .then grub will be gone but xp will be bootable yay

---

### Post by Vipersfate on 2009-05-13
I should've thought of that. Good, makes things easy. I want to select the hard drive I boot off of rather than grub do it for me, it's easier for me to do it that it. Thanks William.

EDIT: Just got it working, thanks so much William, I thought all was lost. It did that a long time ago, and I never was able to figure it out.

---

### Post by Vipersfate on 2009-05-13
Well, unfortunately, fixing windows broke Ubuntu. /cry. Computer just hangs there after selecting the boot device (F12 on my system) and just has a blinking cursor.

---

