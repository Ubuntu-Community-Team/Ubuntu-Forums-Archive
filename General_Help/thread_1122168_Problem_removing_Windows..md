---
title: "Problem removing Windows."
date: 2009-04-10
forum: General Help
---

### Post by Newuser1111 on 2009-04-10
I had Windows Vista, XP, and Ubuntu 9.04 on my Compaq laptop.
Windows Vista broke(I really don't know why) and was using up over 100GB of space. So I decided to remove it and the XP(because without Vista, XP can't boot. And I wasn't using XP very much on there.)

But now my laptop won't start:
```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17
```

---

### Post by Eisenwinter on 2009-04-10
Just reinstall grub from a live environment.

---

### Post by Newuser1111 on 2009-04-10
> **Eisenwinter said:**
> Just reinstall grub from a live environment.
```
root (hd0,4)

Error 21: Selected disk does not exist
```

/ is /dev/sda5

---

### Post by chris4585 on 2009-04-10
[Reinstalling grub is easy]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Newuser1111 on 2009-04-10
> **chris4585 said:**
> [Reinstalling grub is easy]("http://ubuntuforums.org/showthread.php?t=224351")Thanks, it was because I typed "grub" instead of "sudo grub"

---

