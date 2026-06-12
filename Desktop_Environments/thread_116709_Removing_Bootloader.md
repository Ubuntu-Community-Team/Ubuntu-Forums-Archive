---
title: "Removing Bootloader"
date: 2006-01-13
forum: Desktop Environments
---

### Post by johnsoaw on 2006-01-13
Ok I had to edit this post because maybe it wasn't making sense. I have installed ubuntu onto one of my two hard drives present in my machine. The installation detected that I had windows XP running on the other hard drive, so it suggested I install a bootloader on there to let me pick what to boot up with. I wanted Ubuntu to self boot off of its hard drive later, so I removed the other hard drive and just put a self boot on the Ubuntu HD. Now I have a bootloader on the other hard drive that is giving me weird errors, and I don't know how to remove it. Could some one help me with this?
Thanks,
AJ

---

### Post by art on 2006-01-13
I am not completely sure as to how this goes when you have two HDD, I have always had only one. People who know better would correct me, I hope. But I guess you wanna disconnect the one with ubuntu, boot from Windows installation CD, go to recovery console and do a fixmbr. There are other posts on this in the forum, so maybe they'll have a better description. Just look for fixmbr. That should do it.

---

### Post by Xumbi on 2006-01-13
Ok, I *think* I know what you're saying...

You're booting from the windows drive that had grub installed on it, and it's giving you errors because it can't find the drive with Ubuntu installed?

If that is the case, and you just want to remove grub and get back to the regular windows boot process, you'll need to overwrite the master boot record with the windows boot loader (you can't "remove" a boot loader, you can only overwrite it with something else).

I think there are a few ways to do this, but probably the easiest would be by booting the XP install CD.  You can find instructions [here]("http://www.techzonez.com/forums/archive/index.php/t-3975.html").

Hope that helps!

---

### Post by johnsoaw on 2006-01-13
Thanks much, I will check it out.
~AJ

---

