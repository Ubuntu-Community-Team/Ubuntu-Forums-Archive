---
title: "How to manage a new windows install with dual boot"
date: 2006-02-12
forum: Desktop Environments
---

### Post by simone.brunozzi on 2006-02-12
Hi guys,
I'm not sure how to proceed:

I have a computer with win2000 + kubuntu 5.10;

I want to replace win2000 with winXP, but I'm not sure how to do that.

If I start the winXP cd, I can install in the same partition now occupied by win2000, but... what happens to grub??
How can I (after winXP installed) fix the grub and have again the choice between winXP and ubuntu??

Is this process risky for my data in the linux partitions??
(Consider that I'm confident with partitioning and installing processes).

Thanks a lot for any help!!!

Simone

---

### Post by Ocxic on 2006-02-12
the only thing that will be ovrwritten will be grub, wich is ok, all you'll have to do is re-install grub from the live cd. or as an alterative you could just disable/remove your ubuntu drive from the computer, install windows, reconnect the drive, and run sudo update-grub once your back into ubuntu and you windows install will be added to the list.

---

### Post by chettyk on 2006-02-12
You may want to look at the article "Give Multiple Distros the Boot" that appeared in the Nov. 2005 (issue #8 ) of TUX, the free e-magazine for the new linux user. You can download a PDF of that issue from:
**[http://www.tuxmagazine.com/]("http://www.tuxmagazine.com/")**

---

### Post by simone.brunozzi on 2006-02-13
Thanks all of you guys,
things are pretty straightforward, as I suspected.

I think I'll go with installing windows, and then setting up again GRUB with a liveCD.

Cheers,

---

