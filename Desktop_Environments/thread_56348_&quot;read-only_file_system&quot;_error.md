---
title: "&quot;read-only file system&quot; error"
date: 2005-08-12
forum: Desktop Environments
---

### Post by ganbaru on 2005-08-12
Hi 

Without any warning my programs crashed; i restarted firefox but it wouldn't load and i got this error message:

postdrop: warning: mail_queue_enter: create file maildrop/495853.10129: read-only file system

and i had to reboot and do "fsck" manually and reboot...

this is NOT the first time...

any help please?
Thanks a million in advance

---

### Post by fresco on 2005-08-12
There is an option in fstab. Mine looks as follows:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1

I think that your volume had errors so system remounted it as read-only...
Maybe deleting errors=remount-ro will fix the situation, but I don't know, is it safe or no. Maybe you should run fsck -c? Try it!

---

