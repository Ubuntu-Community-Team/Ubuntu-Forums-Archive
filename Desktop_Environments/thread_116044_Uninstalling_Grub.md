---
title: "Uninstalling Grub"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Akya on 2006-01-11
i got a grub error, grub error 17 and i cant fix it so ive decide i want to just uninstall grub and re-install it but i dont know if this would mess up my partitions  or earse my data and if it wont then how can i do it

---

### Post by blackbeastofaarrgh on 2006-01-11
Alright. Are you dual-booting with Windows XP? If so, do you have the installation disk? If you do, boot from it, go into the recovery console by pressing "R" when everything loads, repair your Windows partition, wait... type "fixmbr", type "y", poof.
But, if you're not dual-booting, forget I said anything. :P

---

### Post by jerrykenny on 2006-01-11
Error 17 is grub doesnt recognize the file type . . . 

Have you manually edited your menu.lst ?

If so remember that grubs numering system is a bit awkward,

eg, first hard drive is hd(0,?)

second hard drive is hd(1,?)

etc

the first primary partition on a drive is hd(?,0)

2nd primary is hd(?,1)

You havent installed onto a strange filesystem have you ?  ext2 ext3 and reiserfs are good . . .

---

### Post by Akya on 2006-01-11
no i havent edited my menu.lst i was running linux then i put in a new hard drive and installed windows and now i cant even get on the hard drive from windows

---

### Post by catalina on 2006-01-12
Hi,

I had a similar problem installing breezy on one of my laptops.  I actually had a ghosted cd on win 2000 pro, ghosted the hd then tried reinstalling ubuntu and it worked.  It was not a problem with ubuntu but a problem with how I installed ubuntu.  You may not have the time to do this if you have to install the whole os again, but worth a try if nothing else works.

I am just a newbie so take my advice at face value.
Dean.

---

