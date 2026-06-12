---
title: "Windows on Dell Precision"
date: 2009-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rickcjmac on 2009-09-08
I have Ubuntu 9.04 on all of my computers. I love it, but after putting Ubuntu 9.04 on my brother's computer he decided he doesn't like it and he wants Windows back on it. 

I have the disk for Windows XP OS (that's what was on it before), but when I try to install it, all it does is freeze up. 

I clicked the option to check compatability online, and a message came up saying that Windows encountered an unexpected error and must shut down. 

Any help is appreciated.

Oh, and because the hard drive is so small, when we installed Ubuntu we didn't partition the drive, we just installed Ubuntu as the primary OS.

---

### Post by SoftwareExplorer on 2009-09-08
At what point does it freeze?

---

### Post by QIII on 2009-09-09
You will likely have to use the LiveCD, wipe out the Linux partitions and reformat the entire disk as a single NTFS partition.

The "other" OS can't comprehend the fact that there might, just might, be other formats out in the world outside of Redmondia, so it gets confused and pukes.

---

### Post by rickcjmac on 2009-09-13
I put the cd in, open the install.exe with WINE, options show like install, check compatability, etc... I choose install then it freezes.

---

### Post by SoftwareExplorer on 2009-09-13
> **rickcjmac said:**
> I put the cd in, open the install.exe with WINE, options show like install, check compatability, etc... I choose install then it freezes.
Wait, you're tying to install windows from linux? I wouldn't expect a Microsoft application to run on wine without a lot of whining. (Pun somewhat intended) I think it will mean that Microsoft is disparate when that works! :D To do what QIII said you would use the ubuntu CD. 

One thing: Your windows CD might be scratched, so if you happen to have another one somewhere else by chance you might see if it won't freeze on you. You would boot from the CD to install windows normally, instead of inside linux.

---

### Post by community nerd on 2009-09-13
Every time i install windows i just reboot my computer and go to the bios and boot from the cd.

---

### Post by rickcjmac on 2009-09-19
> Every time i install windows i just reboot my computer and go to the bios and boot from the cd.

That worked perfectly :P Thank you guys a ton. He is happy and back with Windows (the loser) :)

---

