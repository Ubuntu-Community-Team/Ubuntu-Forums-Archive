---
title: "Dell Inspiron B130 Installation problem"
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by rcvv on 2007-12-29
My notebook (a Dell Inspiron B130 ), first had Windows Xp Home. After that I installed Ubuntu 7.10. Now I really need to return to XP for my work. So I completely formatted my hard disk to blank. Now when I try to install windows, the bootable disc is just starting off and immediately giving me a blue screen error. That Windows disc works on all other systems. I am told that linux has changed something in my BIOS or something. Now I really need XP for work:(. SO somebody please help, Thank you very much.

---

### Post by jdholifield on 2007-12-29
I could be wrong, but I believe that Ubuntu ( Linux in general ) is different from Windows in that in a Linux system the BIOS is only used to start the boot loader, once the boot loader is running I think Linux probes and accesses the hardware directly without the BIOS.  Thats my extremely dumbed down version as I understand it, so take that for what its worth.

In any case, its doubtful that Linux changed anything in your computer's BIOS.

You might be better off asking for help in a Window's type support forum.

At the very least, you could boot into your computer's BIOS, then restore the defaults and save, then exit and try your Windows install again.  That would at least rule out the possibility that Linux had changed something in your computer's BIOS.

Good luck.

---

### Post by spiff95 on 2007-12-29
Most Dell computers have a "Rescue" partition and a "diagnostic" partition. To access it, you have to press and hold a key combo like CTRL+F8 (to find out the exact combo, you can look it up on the support pages on the Dell web site). Use the key combo when the computer first boots, before it tries to start the OS. Then choose the restore option and follow the prompts.
Note that this will only work if you didn't format those partitions when you installed Ubuntu.

Another thing you might try so you can keep your Ubuntu installation is to install VirtualBox and run your Windows progs on it.

Hope this helps.

---

