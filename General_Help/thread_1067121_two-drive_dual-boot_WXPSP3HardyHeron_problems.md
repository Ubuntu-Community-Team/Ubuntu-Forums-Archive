---
title: "two-drive dual-boot WXPSP3/HardyHeron problems"
date: 2009-02-11
forum: General Help
---

### Post by scjwm on 2009-02-11
Greetings All --- 

I have installed "two-drive dual-boot WXPSP3/HardyHeron" on two machines now and both work great EXCEPT that WXP keeps resetting itself five time zones at cold boot.  That is exactly the difference between my local time and GMT.  Hardy is unaffected and remembers the local time.

One setup uses two SATA drives with Ubuntu on the primary drive, the other uses two IDE drives (with cable select) with Ubuntu on the master drive.  I have checked carefully for viruses, checked the BIOS settings, and applied all the WXP "fixes" I could find on the Internet.

It appears to be somehow related to moving WXP to a secondary drive location.  Has anyone else bumped into this problem?

PS - two other two-drive dual-boot machines done the old way with WXP on the primary and the MBR modified work fine with no time zone problems.

I am stumped.  Any help would be greatly appreciated.....

---

### Post by caljohnsmith on 2009-02-11
Scjwm, next time please start your own thread, because your problem is entirely unrelated to this thread. About your problem, if you do:
```
cat /etc/default/rcS | grep -i utc
```
Does that show "UTC=yes"? If so, change that file to use "UTC=no" and that might fix your problem.

---

### Post by scjwm on 2009-02-11
I apologize -- that was my first ever attempt to place anything in/on a forum.  I will get it right the next time!

Indeed it does show utc=yes and I will make the change and see what happens.  Thank you very much....

---

### Post by bapoumba on 2009-02-11
Moved to their own thread.

---

### Post by scjwm on 2009-02-11
CalJohnSmith -- You nailed it!!!!  Both Ubuntu and WXP are now remembering which time zone we are in.  Thank you again -- scjwm.

---

### Post by caljohnsmith on 2009-02-11
Glad to hear that did the trick; cheers and enjoy Ubuntu and Windows. :)

---

