---
title: "try copy home directory to windows disk."
date: 2009-05-04
forum: General Help
---

### Post by JohnPta on 2009-05-04
I try to copy my "home" directory to my windows disk. Under normal conditions it tells me "No permission" so I went in to terminal logged in as root user and loaded "gksudo nautilus" and tried the same again and still I get the message "you do not have the permission".

How can I copy my "home" directory?? in order to save my setup before I will upgrade to 9.04??

---

### Post by dcstar on 2009-05-04
> **JohnPta said:**
> I try to copy my "home" directory to my windows disk. Under normal conditions it tells me "No permission" so I went in to terminal logged in as root user and loaded "gksudo nautilus" and tried the same again and still I get the message "you do not have the permission".

How can I copy my "home" directory?? in order to save my setup before I will upgrade to 9.04??

If your "windows disk" is FAT32 then you are wasting your time, it does not support the permissions that Linux requires - even NTFS would be problematic.

If you want to back up your /home then boot off a Live CD and make a tarball of it - you can copy that to a Windows filesystem otherwise create a Linux filesystem somewhere and use that.

---

