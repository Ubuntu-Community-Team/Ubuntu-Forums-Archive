---
title: "[SOLVED] ready to drop Windows - dual-boot question"
date: 2008-11-27
forum: Desktop Environments
---

### Post by TripitakaUK on 2008-11-27
A little forward planning...

I have a system that has 5 drives and is ex-Windows. I dual boot currently.

(hd0,1) is the current boot partition and has the WinXP on it.
(hd3,0) is the Ubuntu install that dual boots.

I want to ditch the XP partition completely now but retain an option to dual boot to an as yet empty partition (hd3,3) which will be an ubuntu sandpit environment.

What steps do I need to take for this to work properly?

Thanks,

Mark.

---

### Post by ajgreeny on 2008-11-27
If you did what is the default when you installed ubuntu, the MBR of windows will now contain grub, so when you get rid of windows you may also remove grub.  That is not a major problem as grub can be easily restored using the ubuntu live CD.  See attached txt file

With regard to your other point about retaining the ability to boot to another, as yet not installed OS of ubuntu, don't worry.  When you install it the new system, being ubuntu will find and add the old ubuntu to the new grub menu.lst file, and if you have not already done so, will itself restore grub to the whole system.

---

### Post by TripitakaUK on 2008-12-02
Superb job! Worked flawlessly.

Thanks for your help.

Mark.

---

