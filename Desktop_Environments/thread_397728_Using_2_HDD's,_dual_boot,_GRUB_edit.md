---
title: "Using 2 HDD's, dual boot, GRUB edit"
date: 2007-03-31
forum: Desktop Environments
---

### Post by Dan Kay on 2007-03-31
Hey guys....
I know this has been beaten to death....but here is my situation.

I have WinXP and Ubuntu Edgy installed on an IDE drive...Grub is installed on that drive (obviously), and it's split into 2 partitions.....it dual boots fine using GRUB...no problems.
On that drive I believe WinXP is (hda) and Ubuntu is (hdb), although I'm not exactly sure how it's exactly identified. I know Grub must be identified also somehow....right?

I unpluged my IDE drive and installed a seperate SATA drive in my computer and installed Vista on it.

Now I want to boot to ANY OS ( guess any drive) using GRUB.

I think I need to make my IDE drive the first boot drive so I can see GRUB come up and make the SATA drive the next to boot (in BIOS).....OK.....

How do I check to see the EXACT OS identification on my IDE drive? (so I can edit GRUB properly)

And what code should I try in editing GRUB to make this all work correctly??

A step-by-step guide would sure help! (I'm a nOOB big time)

Thanks for your help!

---

### Post by benerivo on 2007-03-31
I believe the answer would be to set the IDE drive as the primary and make sure the BIOS is set to try and boot to it first. When in Ubuntu, you need to edit the /boot/grub/menu.lst file and add a section to the end. Here is the classic XP entry in grub...
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

The (hd0,0) bit says that it is on the primary (0) hard drive and it is in the first (0) partition. I would add an entry for vista exactly as the above example, but with (hd1,0). You may give it any title you wish rather than Windows XP, and It will become an option on booting your PC. Post the error message if it fails...

---

### Post by Dan Kay on 2007-03-31
I will.......thanks for your help.

---

