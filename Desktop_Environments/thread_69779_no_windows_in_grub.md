---
title: "no windows in grub"
date: 2005-09-27
forum: Desktop Environments
---

### Post by tlaloc1234 on 2005-09-27
I'm using Ubuntu for about a week. Everything is perfect, but this morning Windows XP desapeared from the boot list. I know it's still there, but can't access that. I intend to get rid of windows, but not yet! 

I have an acer travelmate laptop. Windows is in HDA2, Ubuntu is in HDA3. 

What can I do?

(thanks in advance, sorry for my poor English, I'm brazilian...)

---

### Post by brentoboy on 2005-09-27
pop in your xp cd and boot to recovery console

[http://support.microsoft.com/default.aspx?scid=kb;EN-US;314058](http://support.microsoft.com/default.aspx?scid=kb;EN-US;314058)

use the fixmbr command to restore your windows boot record.

this will hose your linux bootloader (grub).

So pop in your ubuntu CD and use it install grub.

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by tlaloc1234 on 2005-09-27
Ok, I'll try that. Thank you!

---

