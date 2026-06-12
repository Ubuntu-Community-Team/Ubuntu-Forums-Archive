---
title: "Discussion - https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Support threads should be posted in normal forums.

Thank you.

---

### Post by RAJESHKSV on 2012-10-08
Hi All, 

I just wanted to add a small point here. Sometimes before restoring Windows 7 Bootloader, i.e., before running those two commands, One has to check if main partition (C drive for most people) is active or not. If not first we need to set it active and then run the two commands given in the page. Then only it will work. Can we please add this line as well that one has to check the partition if its active or not and provide a link for the same ?  This sceanario(marking C partition active) is important when user have windows recovery partition(Say D drive) and he deleted it to install Ubuntu on it

Thanks
Rajesh KSV

---

### Post by coffeecat on 2012-11-19
> **RAJESHKSV said:**
> Sometimes before restoring Windows 7 Bootloader, i.e., before running those two commands, One has to check if main partition (C drive for most people) is active or not. If not first we need to set it active and then run the two commands given in the page.

A valid point, but the wiki commands include fixboot (or bootrec.exe /fixboot) which I believe will set the Windows boot partition as active anyway.

I've added a fourth section for restoring the bootloader using an Ubuntu live CD. This will hopefully be useful for those needing to restore the Windows bootloader but without access to a suitable Microsoft disc for running the Windows recovery console commands - OEM restore discs won't do. I've been involved in a number of threads where the OP has been in this situation.
 
I've included a bit on checking that the Windows partition is active in the new section because the Ubuntu terminal commands are only a substitute for fixmbr and not fixboot.

Formatting is a bit rough atm but I'm working on that.

---

