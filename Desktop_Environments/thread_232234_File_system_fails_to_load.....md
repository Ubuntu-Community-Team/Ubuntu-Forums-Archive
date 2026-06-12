---
title: "File system fails to load....?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by dave55man on 2006-08-08
For some reason when i try to boot up linux it tells me that my File system (hda2 for me) has errors on it and that e2fdsck can't automiatically fix them... So it tells me to go into maintence mode   and run the check myself, which i did, but than when i do that it tells me that my superblock is bad and then tells me to use an alternative superblock... which i also did but it then gives me the same message... whats goin on.

Also i have a dual boot system with windows XP on it and my laptop was working fine just the other day, so i'm really stuck here.
Can someone help?

....nvm.... i just fixed the problem... it turns out that i need to specify the device by using /dev/hda2, not just hda2, and i also found out that my main problem was a bad inode, oh well... it's fixed now.  I guess i'm still a noob at linux.

---

