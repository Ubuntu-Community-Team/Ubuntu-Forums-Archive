---
title: "Edubuntu - Forgot root password"
date: 2009-01-07
forum: General Help
---

### Post by jts01 on 2009-01-07
This is a really stupid question, and I can't believe I have to ask it... here goes...

I have Edubuntu installed on my kids' computer, I put it on here about 7 months ago or so... Well, today I hopped on in an attempt to update the OS and the other updates out there and for the life of me, I cannot remember the root password.  I've tried everything I would've logically put, but no dice.  Is there anyway to reset it or find where it could be referenced and/or visible?  I feel like an idiot, but I clearly must've thought it'd be something I'd remember.  

Any help would be greatly appreciated.   

Thanks in advance,

John

---

### Post by mssever on 2009-01-07
> **jts01 said:**
> This is a really stupid question, and I can't believe I have to ask it... here goes...

I have Edubuntu installed on my kids' computer, I put it on here about 7 months ago or so... Well, today I hopped on in an attempt to update the OS and the other updates out there and for the life of me, I cannot remember the root password.  I've tried everything I would've logically put, but no dice.  Is there anyway to reset it or find where it could be referenced and/or visible?  I feel like an idiot, but I clearly must've thought it'd be something I'd remember.  

Any help would be greatly appreciated.   

Thanks in advance,

John
First off, there is no root password unless you explicitly created one. Try booting into recovery mode. If you get in, then there was no root password.

If you did set up a root password, boot from a live CD, mount your root partition somewhere (for simplicity's sake, I'll assume you mounted it on /mnt), then type ```
sudo chroot /mnt
```You should now have a root shell on your installed filesystem. Just issue passwd and you can reset the password.

---

