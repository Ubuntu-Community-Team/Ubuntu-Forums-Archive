---
title: "reseting boot and shutdown image"
date: 2008-12-07
forum: General Help
---

### Post by sigurnjak on 2008-12-07
I was trying changing default boot and shutdown image and am not happy with results . How do i change everything ( boot and shutdown image ) to nice orange default scrollbar with  Ubuntu logo ?

Now i did more damage!

So tried to use start up manager and choose set to default and now i do not have my current kernel listed but default one which is uninstalled .  As of now i can boot in xp  but my menu.lst is messed up with old info .
How do i refresh and update menu.lst from cli  to reflect my recent kernel since all i get when choosing kernel is a file not found since is uninstalled  and new one is in its place .

I did try grub reinstall but all i get is same menu list.

---

### Post by sigurnjak on 2008-12-07
So it is solved !
I used this guys menu.lst [http://ubuntuforums.org/showthread.php?t=1004399](http://ubuntuforums.org/showthread.php?t=1004399)
and added it to mine . Then i changed my root id and hd  location info , removed obsolete kernel info and saved it . after rebooting i had my good kernel listed as default and xp on the bottom and now i am writing this from  Ubuntu .

---

