---
title: "Removing Mounted Partition Drive Icons From Desktop"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mcescher on 2005-12-09
I have mounted my Windows XP NTFS and FAT32 data partitons (after following the Ubuntu guide). My problem is that they appear as icons on my desktop now.

I would like to remove these so that the icons do not appear on my desktop.

Can anyone tell me how I can do this?

---

### Post by canadianwriterman on 2005-12-09
I'm not at my Ubuntu box right now, but I believe you can go to **Applications > System Tools > Configuration Editor > apps > nautilus **and somewhere in there is a checkbox for showing mounted drives on the desktop. I could be wrong.

---

### Post by blair on 2005-12-09
I have same question and goal. I looked in nautilus and several other locations but don't see any specific mention of display/partition or icons, or anything to that effect.  

I do see a "display internal hard drives" option under /system/storage but it does seem to be having any effect. I have a dual boot Win98 (FAT)/Ubuntu system and would expect to see hda1 showing up or not when I toggle this option and restart Gnome. Is this the correct setting or it it somewhere else? thanks.

---

### Post by canadianwriterman on 2005-12-09
[QUOTE=blair]I have same question and goal. I looked in nautilus and several other locations but don't see any specific mention of display/partition or icons, or anything to that effect.  

I do see a "display internal hard drives" option under /system/storage but it does seem to be having any effect. I have a dual boot Win98 (FAT)/Ubuntu system and would expect to see hda1 showing up or not when I toggle this option and restart Gnome. Is this the correct setting or it it somewhere else? thanks.[/QUOTE]

The setting is not in Nautilus itself. I believe it's in **Applications > System Tools > Configuration Editor > apps > nautilus**.

---

### Post by out180 on 2005-12-09
[QUOTE=canadianwriterman]I'm not at my Ubuntu box right now, but I believe you can go to **Applications > System Tools > Configuration Editor > apps > nautilus **and somewhere in there is a checkbox for showing mounted drives on the desktop. I could be wrong.[/QUOTE]

Correct.

volumes_visible

Remove the check, loose the mounted drive icons.

---

### Post by mcescher on 2005-12-09
Worked great. Thanks for the help.

---

