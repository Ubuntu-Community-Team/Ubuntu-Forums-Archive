---
title: "GDM won't come up, gnome won't load"
date: 2007-08-19
forum: Desktop Environments
---

### Post by Epistis on 2007-08-19
Ok, I can't really tell you what I did to make this happen. I just left Ubuntu running, with XP in VirtualBox on a dual-head display (ubuntu on LCD, XP on CRT...it was nice :) ) overnight, and when I woke up, it had frozen, but it still responded to an emergency sync, unmount, and reboot.

Now, the X server comes up, but I get the plain background and the white circular animated cursor, and it never proceeds.

Admittedly, I was messing with my xorg.conf but I had it working fine, even after a reboot, when I went to bed. Anyway, I've tried restoring the backup. Problem remains.

I'd give you more information, if I really knew what needed to be provided. If you think you can help and need more info, please feel free to ask.

Thanks in advance!

---

### Post by Happy_Man on 2007-08-19
Hmmm... boot recovey mode, and enter: ```
sudo /etc/init.d/gdm start
``` and see what happens.

---

### Post by Epistis on 2007-08-19
That leads to the same problem. :(

However, I tried startx after logging in to a text console and gnome successfully started up, so it must be GDM that is broken.

*sigh*

Any ideas on how to repair it?

---

### Post by Doomguy0505 on 2007-10-25
I get this problem with 7.10 now

---

### Post by Epistis on 2007-10-25
> **Doomguy0505 said:**
> I get this problem with 7.10 now

That's why I use PCLinuxOS now. I still love Ubuntu, and I miss it. I will probably install it alongside PCLOS when I can free up some more hard drive space.

---

