---
title: "I loose write permision in home directory"
date: 2005-12-25
forum: General Help
---

### Post by bpasdar on 2005-12-25
Lately I have noticed that after my system has been on for 24-48 hours, I all-of-the-sudden loose write permision to my home directory content.  The only fix is a reboot and all starts to work again.

I especially notice this when kmail pops up and says that it has no write permision to:

~/.kde/share/config/kontactrc

When I look up permisions:

-rw-------  1 bpasdar bpasdar 2861 2005-12-24 12:12 kontactrc

However when I edit kontactrc via VI, it says it is readonly.

My only quasi-unique setup factor is that /home/bpasdar is a SymLink to /spc1/home/bpasdar.  This however has worked for me for years through many linuces (redhad, yellowdog, fedora, mandrake, etc...)

Any suggestion as to what could be happening.

Thanks

Babak

---

### Post by gruepig on 2005-12-25
Why not just make /spc1/home/bpasdar your home directory? (sudo usermod -d /spc1/home/bpasdar bpasdar)

---

### Post by mlomker on 2005-12-26
Is it all of your files or just that one?  I'm not sure how rebooting would solve a permissions problem.  

Generally when permissions get reset on a file like that it is because a process running as **sudo** writes to the file and resets the permissions to root.  Do you run any email-related applications as root?

---

### Post by bpasdar on 2006-04-10
THank you for the response.  It ended up being a hardware issue with some bad blocks on my hard disk.

---

