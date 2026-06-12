---
title: "Grub takeover."
date: 2009-01-17
forum: General Help
---

### Post by dragos240 on 2009-01-17
I was installing ubuntu for my brother becuase he hated windows, i partitioned it so that vista still worked but ubuntu could as well, so i did that, and ubuntu worked great, now dad came in the room to help us connect to the internet on it, and he said "whats this" i said "whats what?" he said that i need administrator privalages to install ubuntu, and i replied "No, why would you?" The he knew i partitioned it, he was mad at me becuase mom messed up her own computer not knowing what she was doing and couldn't boot into windows, dad and mom blamed me, anyways my dad got furious, he said to take it off or i would loose my computer, so i shut down the computer and booting into parted magic, i erased the ubuntu partition and grew the vista partition back up to what it was before. But when i saved, i shut it down and booted up and grub was still the main thing, and sadly the menu.lst or something was in the ext3 ubuntu partition too, now i need to revert back to the original vista menu for a bootup. I think i fixed it, but just to be sure, someone please help.

---

### Post by upchucky on 2009-01-17
google vista fix mbr to get rid of grub if u are not gonna use linux, it is sad that so many are brainwashed by windows. one day u r gonna have u own pc and can boast to dad that u can do things better and cheaper on it.

---

### Post by dragos240 on 2009-01-17
> **upchucky said:**
> google vista fix mbr to get rid of grub if u are not gonna use linux, it is sad that so many are brainwashed by windows. one day u r gonna have u own pc and can boast to dad that u can do things better and cheaper on it.

Oh i wish, but my dad doesn't understand why ubuntu is better, luckily my dad lets me keep my ubuntu. But thx

---

### Post by adult swim on 2009-01-17
if you havent found it yet, you need to boot the vista install cd and get to a command prompt.  then run ```
bootrec /fixboot

bootrec /fixmbr

exit

``` and reboot

---

### Post by dragos240 on 2009-01-17
> **adult swim said:**
> if you havent found it yet, you need to boot the vista install cd and get to a command prompt.  then run ```
bootrec /fixboot

bootrec /fixmbr

exit

``` and reboot

thank you

---

