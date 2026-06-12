---
title: "cannot change to root"
date: 2005-01-12
forum: Desktop Environments
---

### Post by Benignsoldier on 2005-01-12
Hello im a novice at this whole ubuntu thing...although i did do gentoo for a while (with the help of a friend) so i know general commands...i think...

anyways, when i get lazy with my mouse i should be able to open terminal and access root with su as a user...well i discovered i cannot add myself to wheel at all, therefor cannot access root as a user, the only way i can find is to click on apps>systemtools>root terminal. There should be that faster way...help? why cant i add myself so i can log on as a user? 

thanks  [-o< 


kurt

---

### Post by hashimoto on 2005-01-12
[QUOTE=Benignsoldier]Hello im a novice at this whole ubuntu thing...although i did do gentoo for a while (with the help of a friend) so i know general commands...i think...

anyways, when i get lazy with my mouse i should be able to open terminal and access root with su as a user...well i discovered i cannot add myself to wheel at all, therefor cannot access root as a user, the only way i can find is to click on apps>systemtools>root terminal. There should be that faster way...help? why cant i add myself so i can log on as a user? 

thanks  [-o< 


kurt[/QUOTE]
 Ubuntu uses "sudo" by default. You got to enable root if you want to "su". See instructions: [http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

BR
Hashimoto

---

### Post by randy on 2005-01-12
sudo -s will also give you a root shell.

---

### Post by ixus_123 on 2005-01-12
This threw me a bit at first but if you sudo open a text editor fro example, it's much easier to edit any system files you might want to like grub, inetab, etc

---

