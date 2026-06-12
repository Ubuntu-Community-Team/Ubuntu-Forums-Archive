---
title: "Grub Error 18 after loss of power"
date: 2006-06-11
forum: Desktop Environments
---

### Post by shredswithpiks on 2006-06-11
After an amazing success with installing Ubuntu 6.06 on my laptop, I decided it should go on my 64bit desktop PC as well.

I can get everything installed just fine, but when I power down and try to boot back up I get a Grub: error 18.

I am using an IDE hard drive, it's the only one and I'm using the entire disk, so it's not like windows is killing the partitions or anything weird like that.

I can reinstall Ubuntu totally and everything will be fine, until a power down.

Reboots are fine, but as soon as power is lost to the system (unplugged, shut down, whatever) I get the same error 18 in grub.

I've reformatted and reinstalled 3 or 4 times today, and the same thing keeps happening.

Help?

---

### Post by dermotti on 2006-06-11
Does it also happen when you reboot?

---

### Post by shredswithpiks on 2006-06-11
No. If I install ubuntu, and restart, everything works fine.

If I shut down, and then turn the computer back on, grub stage 1.5 throws error 18. (After some googling, the error is apparently when grub finds a hard drive that's larger than the BIOS can handle. It's an 80GB hard drive, and obviously the BIOS can handle it (ran windows/suse for a very long time in this machine).

---

### Post by glotz on 2006-06-11
Have a nice .

---

### Post by shredswithpiks on 2006-06-11
period?

:)

---

### Post by glotz on 2006-06-11
Sorry for that, just that we cannot delete our posts on this crazy forum... Just tried to be funny editing my post. (and obviously crashed and burned...)

---

### Post by shredswithpiks on 2006-06-11
I lolled... ~.O

:)

---

### Post by zac1333 on 2006-06-23
Any update on this?  I'm having a similar issue.

---

### Post by glotz on 2006-06-25
Looks like you guys could be in need of a BIOS update. [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

Flashing your BIOS can potentially b0rk your puter, should a blackout occur at the moment or something like that. And you want to be sure that you'll have the correct file to flash them with. I've done it once and all went just fine.

---

