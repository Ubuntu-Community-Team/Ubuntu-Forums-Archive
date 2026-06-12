---
title: "My graphics card has crashed 7.10 Gutsy!!"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by Le Geordie on 2008-01-16
Please please help a new person to the world of linux! 

I have installed (not with out issues) Gutsy on a partition. I have an ATI Radeon X600 card in the dell also (i beleive from reading the posts that ATI cards are a touchy subject!).

Gusty was running fine with Compiz and all the trimmings using the restricted drivers option turned on. Everything great then suddenly when trying to change the skydome image BANG the system froze. Then the ability to run the cube stopped along with other things.

So i restarted system and now the graphics are so mangled it is unusable/unreadable.

Help!! I can i get this system back? What commands may i need in the recovery option?
I was hoping to prove a point to my employers how good linux was and then this happened!

Cheers

---

### Post by karth on 2008-01-16
You can revert to a standard "first run-like" configuration by running ```
dpkg-reconfigure xserver-xorg
``` from the recovery console.

Then you'd just have to reboot and open a normal session, and maybe try to enable the restricted drivers again.

---

### Post by Le Geordie on 2008-01-17
Thanks for that. Tried it got my desktop back again, turned on restricted driver again and system frozen. Restarted and OS couldn't detect card and switched to low graphics mode!!
Ran the command again but only this time the screen res can only be set to 800 x 600! I  know i may need glasses but not that much!

Any further ideas how to fix this problem?

Cheers again everyone

---

