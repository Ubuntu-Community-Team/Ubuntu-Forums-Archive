---
title: "How can I make cdrom executable?"
date: 2005-08-24
forum: Desktop Environments
---

### Post by obladi on 2005-08-24
How can I setup /etc/fstab to enable CD to be executed?

I tried this:
/dev/hdc        /media/cdrom0   udf,iso9660 exec,rw,user,noauto  0       0

But, result is
$mount
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=xxx)

---

### Post by arnieboy on 2005-08-24
[QUOTE=obladi]How can I setup /etc/fstab to enable CD to be executed?

I tried this:
/dev/hdc        /media/cdrom0   udf,iso9660 exec,rw,user,noauto  0       0

But, result is
$mount
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=xxx)[/QUOTE]
what do u mean by cd being executed? if u mean automount, thats enabled by default in ubuntu.
in my /etc/fstab it looks like:
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

