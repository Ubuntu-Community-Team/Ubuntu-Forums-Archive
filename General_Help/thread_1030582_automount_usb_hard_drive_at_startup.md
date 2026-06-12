---
title: "automount usb hard drive at startup"
date: 2009-01-04
forum: General Help
---

### Post by kutlu on 2009-01-04
How can I ensure that usb hard drives (or al removable media) are mounted at startup?

I added following to fstab, but then, there is problem with mounting after plugging-unplugging.

/dev/disk/by-label/FreeAgent\x20Drive /home/kutlu/FreeAgent ntfs-3g defaults 0 0 

I have kde.


Edit: I decided to use another method, I am using pmount. I added it to startup and it works fine with user account.
I cannot mount to desired directory, but I'm fine now.

---

