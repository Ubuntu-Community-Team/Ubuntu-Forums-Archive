---
title: "Dual Boot (XP / Ubuntu): use Windows fonts in Gnome?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Schroeder on 2006-06-26
Hi,

I have a dual boot setup XP/Ubuntu 6.06. Is there any way I can use the Windows fonts installed on the other partition in Ubuntu? I have already installed the Windows corefonts but I want some of the other fonts that are available in my XP. 

Thanks,
Chris

---

### Post by Dubbayoo on 2006-06-27
[QUOTE=Schroeder]Hi,

I have a dual boot setup XP/Ubuntu 6.06. Is there any way I can use the Windows fonts installed on the other partition in Ubuntu? I have already installed the Windows corefonts but I want some of the other fonts that are available in my XP. 

Thanks,
Chris[/QUOTE]

You can just copy the .ttf files to ~/.fonts and gnome will use them automatically. I "think" the names have to be all lower case though; doublecheck.

---

### Post by Schroeder on 2006-06-27
Turns out a symbolic link to my c:\WINDOWS\Fonts directory would suffice but the partition is NTFS so I dont have write access (which is needed for some reason). Copying the Win fonts to /usr/share/fonts/ and updating the fonts cache worked however. Nice. :-D 

Chris

---

### Post by jvictor on 2006-06-27
To add on I did a 
sudo dpkg-reconfigure fontconfig

---

