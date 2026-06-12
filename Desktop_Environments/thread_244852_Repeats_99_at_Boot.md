---
title: "Repeats 99 at Boot"
date: 2006-08-27
forum: Desktop Environments
---

### Post by forkbeard on 2006-08-27
Ok, I don't know what I did to break it but when I rebooted my Ubuntu box on Friday night, it displayed "Li" (as in the first bit of LILO) then just repeated "99 99 99 99 99" for four or five lines before hanging. Seriously, WTF would cause that bizarre of a problem? I hadn't changed the LILO config, and I hadn't even changed anything to try to fix the kernel upgrade issue (the issue was that it wasn't upgrading, but nothing had changed before the start of that problem and the '99' thing) it just did it. I must've broke something but I couldn't imagine what. Any ideas?

---

### Post by reuben on 2006-08-27
This means it is not finding your boot partition (I believe). Log in using your live cd, and then use grub on the command line to install itself to your first hard drive. The guys on #grub on irc were pretty helpful when I had a similar problem.

---

