---
title: "new warty kernel broken"
date: 2005-02-16
forum: Desktop Environments
---

### Post by RastaMahata on 2005-02-16
I recently made a apt-get update, then a apt-get dist-upgrade in warty, and now I cant start X with the new kernel (-5)... what's wrong?

I'm using nvidia.. right now I'm writing from my other kernel (-4)...

---

### Post by Xian on 2005-02-16
[QUOTE=Michael Hipp]The following packages have unmet dependencies:
   linux-restricted-modules-2.6-386: Depends: 
linux-restricted-modules-2.6.8.1-5-386 but it is not installable
E: Broken packages[/QUOTE]
It has to do with the kernel security upgrade that was released today.
A required kernel modules package is not yet in the official repo but will be soon.

Wait for its inclusion before trying the update again.

Ref: [Security Announcement](http://ubuntuforums.org/showthread.php?t=15509)
Ref: [Kernel Upgrade Issue](http://ubuntuforums.org/showthread.php?t=15563)
Ref: [Rebuilding Modules](http://ubuntuforums.org/showthread.php?goto=lastpost&t=15563)

---

