---
title: "GRUB back up ?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by rfruth on 2006-02-11
:-k  Today when I cold booted my breezy box the grub menu came up (as usual) but the screen was blank except for a please wait message - I waited & waited and when nothing happened I hit the reset switch, now grub coughed a error 16 (whatever that is) so I rebooted again, no error from grub this time but the kernel started to load and then panicked so I rebooted yet again this time I got a inconsistent file system message check forced, at 15 percent the screen blanked and stayed that way so I rebooted, got to 25 % & hung so rebooted, got to 40 %, rebooted, then my breezy box came up (yea !) - long story short is there a way to backup just grub or is booting from a breezy CD and running rescue it ?

---

### Post by dcstar on 2006-02-11
[QUOTE=rfruth]:-k  Today when I cold booted my breezy box the grub menu came up (as usual) but the screen was blank except for a please wait message - I waited & waited and when nothing happened I hit the reset switch, now grub coughed a error 16 (whatever that is) so I rebooted again, no error from grub this time but the kernel started to load and then panicked so I rebooted yet again this time I got a inconsistent file system message check forced, at 15 percent the screen blanked and stayed that way so I rebooted, got to 25 % & hung so rebooted, got to 40 %, rebooted, then my breezy box came up (yea !) - long story short is there a way to backup just grub or is booting from a breezy CD and running rescue it ?[/QUOTE]
That looks like a Hard Disk problem, not a Grub problem.

I would be obtaining a new disk ASAP.

---

### Post by rfruth on 2006-02-11
Thanks for the reply dcstar, it *does* sound like a hard disk problem and if it weren't for the fact that the hard disk is (seems ?) fine (even when Grub doesn't load) Id believe it ...

---

### Post by dcstar on 2006-02-11
[QUOTE=rfruth]Thanks for the reply dcstar, it *does* sound like a hard disk problem and if it weren't for the fact that the hard disk is (seems ?) fine (even when Grub doesn't load) Id believe it ...[/QUOTE]
Install the smartmontools and see if the drive is actually "fine", otherwise you run the risk of losing data.

---

### Post by rfruth on 2006-02-11
Hey thanks for the smartmontools tip I installed it (my drive is S.M.A.R.T)

---

