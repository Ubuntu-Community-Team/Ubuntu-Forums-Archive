---
title: "cant find menu.lst"
date: 2009-06-05
forum: General Help
---

### Post by kjh_ngisd on 2009-06-05
I'm not a linux newbie, but I'm not so down on the boot seqence. 
 
I put Wubi on my PC because I was too lazy to re-partition. Life was good. I put Windows7 on the disk and all was good. 
 
UNTIL, I installed my ATI graphics driver in Linux. 
 
Even that was ok. But it caused a hard crash on me today. When I rebooted, Haron can't find menu.lst. I swear, I didn't hide it. 
 
I can't see anything in the "minimal bash shell" it drops me into that will help. 
 
Er... what do I do to get Ubuntu back? 
 
I'm thinking the disk isn't even mounted, btu I can't tell since there's no fdisk from the "limited bash prompt".. 
I guess I can reinstall, but I really hate to. 
 
Is there a link or something that gives me more info about mounting a disk from that grub-like, bash-like prompt?
 
Help?
 
-kevin

---

### Post by VMC on 2009-06-05
On a normal install it is located here "/boot/grub/menu.lst".
I'm not sure how Wubi gets launched. I thought it was from Windows boot loader. Have you checked boot.ini info?

---

