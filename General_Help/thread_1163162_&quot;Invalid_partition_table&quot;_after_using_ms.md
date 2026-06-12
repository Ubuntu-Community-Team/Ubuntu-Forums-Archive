---
title: "&quot;Invalid partition table&quot; after using ms-sys"
date: 2009-05-18
forum: General Help
---

### Post by Sheol66 on 2009-05-18
Hi, in my other computer I have (or used to have ... ) Windows XP and Ubuntu... but I needed to uninstall ubuntu (I dont need it anymore in that one). 

To do it, I followed this guide: [http://users.bigpond.net.au/hermanzone/p18.htm#Replace_GRUB_in_MBR_with_ms-sys](http://users.bigpond.net.au/hermanzone/p18.htm#Replace_GRUB_in_MBR_with_ms-sys)
I typed "ms-sys -f -m /dev/hda1" (the partition with winxp), but when I tried to open Windows XP from the grub menu, it just show me this error: "Invalid partition table"

Then I did something stupid and just messed the things more when typed this: "ms-sys -m /dev/hda".... now the grub menu doesnt show :S

I booted from the live cd and the partition with ubuntu seems to be ok (hda2), but the Windows one appears empty...

How I can fix this mess? I dont think the windows partition can be restored... but there is a way to fix the ubuntu one?

---

### Post by bumanie on 2009-05-18
Your best bet would be to download testdisk from [here]("http://www.cgsecurity.org/wiki/TestDisk") burn it to a live cd and then read the tutorial on the same site and also read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html"). You should be able to rewrite the partition table and as long as you haven't 'played' around too much and haven't over written data, you should get most, if not all your information back with testdisk. it can also be used off the ubuntu live cd, but it is handy to have a dedicated live cd of testdisk too. Good luck. Read up on the procedure first.

---

### Post by Sheol66 on 2009-05-18
Thanks for the answer!
I will try it later and tell you if it works

Any other solution or advice is welcome :P

---

### Post by Sheol66 on 2009-05-18
After using testdisk, the windows xp partition got "fixed"... and i changed it to be the boot
When I restart the pc, the windows logon screen appear and suddenly it got restarted... everytime I do it, happens the same...
Is there a way to fix it? :/

---

### Post by magnificentbird on 2009-11-04
I'm having the same problem. How did you get testdisk to run in Ubuntu? I can't figure that out.

thanks

---

### Post by vegidio on 2010-08-17
Hi,

I created a small guide showing step by step how to restore the Windows MBR using **ms-sys** and how to fix the "Invalid Partition Table" issue using **testdisk**:

[http://forums.lenovo.com/lnv/board/message?board.id=T400_series_ThinkPads&message.id=30899#M30899](http://forums.lenovo.com/lnv/board/message?board.id=T400_series_ThinkPads&message.id=30899#M30899)

Hope it helps. Good luck. ):P

---

