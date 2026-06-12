---
title: "I get to much options when I boot up"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Thanatios on 2006-09-04
Well, I myself am using dualboot to choose between Windows or Ubuntu. When I installed Ubuntu at first, I only could choose out of:
> 
Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (Security mode)

Windows XP

But now, I have a large list of ubuntu's. Even tough I only need 1 (Ubuntu, kernel 2.6.12-10-686)

> Ubuntu, kernel 2.6.12-10-R7
Ubuntu, kernel 2.6.12-10-R7 (Security mode)
Ubuntu, kernel 2.6.12-10-686
Ubuntu, kernel 2.6.12-10-686 (Security mode)
Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (Security mode)

Windows XP

Is there any way to remove all off these, and only let just 2 of them stay?
These ones:
> Ubuntu, kernel 2.6.12-10-686

Windows XP

If so, can you give me a step-by-step guide. I am not so good with doing stuff in linux atm.

Thanks in advance.

---

### Post by someguyouknow on 2006-09-04
Those are suppose to be there. might want to keep them there just in case.

---

### Post by Aggienator on 2006-09-04
You could try commenting out the lines you don't want in /boot/grub/menu.lst. But they probably aren't doing any harm............

Good luck Aggie

---

### Post by Aggienator on 2006-09-04
Srry, just read your original post. So in more detail:

in terminal

 gksudo gedit

Enter your password, gedit will open in su mode (so you can save your changes)

open /boot/grub/menu.lst

(you may want to save as menu.lst.backup just in case

then put hash in front of the lines you don't want and save as menu.lst

good luck

---

### Post by GeirG on 2006-09-04
Those are the different versions of the kernel currently installed, and once you have verified that the latest update works theres usually no reson to have more than the latest set.

The correct way to remove them is to remove (uninstall) the previous versions. Fire up Synaptic from the Administration menu under System (or whatever these menus are called), find the entries for linux-image-2.6.x.x. You will see that there are several versions that are installed. Select the older versions (lover numbers) and select remove.
Remember to apply changes before quitting. Next time you boot, you should only have an entry for the latest entry (plus one for the secure mode)

Might sound scary if your new at this, but trust me its a piece of cake. And once you've done this, there's no end to all the new possibilities that opens up to you ;-)

Good luck

---

### Post by Thanatios on 2006-09-06
Thank you guys (Especially GeirG)
It actually worked! :)

Thanks again, just wanted to say that ^^

---

