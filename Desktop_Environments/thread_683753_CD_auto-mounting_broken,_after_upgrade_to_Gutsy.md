---
title: "CD auto-mounting broken, after upgrade to Gutsy"
date: 2008-01-31
forum: Desktop Environments
---

### Post by tbraun on 2008-01-31
Hello!

I recently upgraded from Feisty to Gutsy. Before, auto-mounting of CDs worked like a charm. Now, it's broken. I insert a data CD and the usual CD icon doesn't appear on the desktop, and not a single message gets printed in /var/log/messages.

It's still possible to manually mount the CD:

[INDENT]sudo mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
[/INDENT]

And then the icon appears on the desktop, and I can normally open it and explore the CD's contents. But because it wasn't auto-mounted by/for/as the current user, I cannot right-click on it and select 'eject'. It tells me I don't have the permission to do that. I need to do a 'sudo umount ...' and then type eject.

Anyway, it would be great to get automount back. I looked in /etc/groups and I am in the cdrom group.

Any idea how to fix this?

Thank you very much...

---

### Post by tbraun on 2008-02-04
bump? Anyone, please?

---

### Post by seventhc on 2008-02-05
can you post the output of this:
```
sudo gedit /etc/fstab
```
Also check under '*System>Preferences>Sessions* and make sure the '*Volume Manager*' has a check next to it.

---

### Post by tbraun on 2008-02-05
Hello!

The relevant entry /etc/fstab says:

[INDENT]/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
[/INDENT]

'Volume Manager' is checked in the Sessions. Automounting of all other things (such as USB drives) works perfectly.

When I go to Places->Computer, I can see the CD drive (whether I have a CD in it or not). If a CD is inserted, I can then go there and right click, and select 'Mount'. The CD will then be mounted without problem, its icon appears on the Desktop.

So, it doesn't seem to be a permission problem or a hardware problem or anything like that. It's just that automounting of the CD doesn't seem to work.

---

### Post by seventhc on 2008-02-05
My fstab reads like this:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
``` you might try adding exec as in mine, maybe that will fix it.

---

### Post by tbraun on 2008-02-05
> **seventhc said:**
> My fstab reads like this:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
``` you might try adding exec as in mine, maybe that will fix it.

Tried that, added that. No difference, though.

---

