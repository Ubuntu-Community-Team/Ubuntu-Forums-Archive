---
title: "Buffer I/O Error on install"
date: 2009-01-28
forum: General Help
---

### Post by Jaded Misanthrope on 2009-01-28
When I try to install Ubuntu 8.10 from the CD, I get a series of errors that go something like 'buffer I/O error on device x' (the device being sda1 if I recall correctly). This happens not only on my laptop but a desktop in my house as well. How could I fix this?

---

### Post by nawitus on 2009-01-28
The problem is most likely with the CD. Burn another Ubuntu cd at the slowest possible speed. I had the same problem when I first installed Ubuntu, I used the max speed to burn the CD which resulted in error(s) while installing. You can also google since the error is quite common.

[http://www.letmegooglethatforyou.com/?q=buffer+I%2FO+error+on+device+ubuntu](http://www.letmegooglethatforyou.com/?q=buffer+I%2FO+error+on+device+ubuntu)

---

### Post by Jaded Misanthrope on 2009-01-28
I have tried multiple CDs, some burnt at speeds as low as 4x and still get the errors.

---

### Post by Jaded Misanthrope on 2009-01-28
The Google search didn't return anything significant (not that I could see, anyway); does anyone have something else?

---

### Post by Jaded Misanthrope on 2009-01-29
Sorry to bump, but this issue is really annoying. Surely somebody has at least an idea of what's happening?

---

### Post by bsmith1051 on 2009-01-29
Try a different CD drive in the desktop.  I had the same problem and even though I'd used my original drive to burn and test the CD, it gave errors during installation (I swapped-in a new hard drive).  After I also replaced the CD drive it then worked.

It's really annoying, a bug really, that a drive can pass the "Test Media" test on the first install screen, yet still fail during the actual installation.  Maybe it's a driver problem, e.g., the test uses the most generic/compatible driver but then the install tries to optimize performance and use a faster (potentially incompatible) driver?

Once you have one working install you can create a bootable flash-drive and use that on the laptop.  Actually, there are 3rd-party tools to do that from Windows, too.  But there's one built-in to Ubuntu 8.10.

---

### Post by Jaded Misanthrope on 2009-01-29
My laptop doesn't support USB booting to my knowledge. Considering that I get the exact same error burning it on either the desktop or laptop and trying to install it on either, I don't think that the drive will be the issue but I'll try when I get one. What you're saying basically boils down to by a new CD drive and / or HDD unless I'm misinterpreting it. Brilliant. (no anger directed at you; it's just incredibly damn irritating)

---

### Post by bsmith1051 on 2009-01-29
You don't need a new hard-drive, that was just part of the procedure I had used.  But I would definitely try another CD drive on the desktop computer.

Also, have you tried doing the Check Media test on the initial CD boot-menu?

---

### Post by Jaded Misanthrope on 2009-01-30
> **bsmith1051 said:**
> You don't need a new hard-drive, that was just part of the procedure I had used.  But I would definitely try another CD drive on the desktop computer.

Also, have you tried doing the Check Media test on the initial CD boot-menu?

I seem to remember the check media spouting I/O errors, but I'll have a  look anyway.

---

