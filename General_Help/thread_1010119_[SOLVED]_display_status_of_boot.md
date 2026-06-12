---
title: "[SOLVED] display status of boot ?"
date: 2008-12-13
forum: General Help
---

### Post by ieee488 on 2008-12-13
I have just installed Ubuntu 8.04 on my Dell Latitude D400 laptop in dual boot with Windows XO.

I notice on boot that the screen remains dark for about 40 seconds. I can hear the hard drive being accessed but the screen is dark. For 5-10 of those 40 seconds the laptop does nothing no sound then the hard drive starts going.

I also don't understand why it does this since on my desktop which has P3 1GHz and 512MB RAM the boot up seems to be faster than this laptop with P3 1.4GHz and 1.25GB RAM.

Any ideas why the screen is blank for so long and also any ideas on how I can speed things up?

---

### Post by Titan8990 on 2008-12-13
Highlight the grub option you use to boot Ubuntu. Hit "e" to edit it. Highlight the kernel like and hit "e" again. 

Delete the words "quiet" and "splash" from the end of that line and hit enter.

Then press b to boot Ubuntu. This may give you some more useful messages.

---

### Post by ieee488 on 2008-12-13
Thanks.

Doesn't look like anything usual is happening during the boot.

Odd that the desktop starts up faster.

---

