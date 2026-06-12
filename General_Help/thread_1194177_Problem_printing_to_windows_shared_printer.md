---
title: "Problem printing to windows shared printer"
date: 2009-06-22
forum: General Help
---

### Post by lsutiger on 2009-06-22
I am connected to a Windows shared printer through samba. I am getting an error that states:
```
Failed to print document
Can't prompt for authorization
```
I run dmesg and get the following:```
[1720489.839816] type=1503 audit(1245677356.464:799): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=16846 profile="/usr/sbin/cupsd"
[1720489.930009] type=1503 audit(1245677356.556:800): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=16846 profile="/usr/sbin/cupsd"
[1720490.020199] type=1503 audit(1245677356.648:801): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=16846 profile="/usr/sbin/cupsd"
[1720490.020259] type=1503 audit(1245677356.648:802): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=16846 profile="/usr/sbin/cupsd"
[1727858.181641] type=1503 audit(1245684724.809:803): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=19634 profile="/usr/sbin/cupsd"
[1727858.181676] type=1503 audit(1245684724.809:804): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=19634 profile="/usr/sbin/cupsd"
[1727858.404473] type=1503 audit(1245684725.032:805): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=19634 profile="/usr/sbin/cupsd"
[1727858.494702] type=1503 audit(1245684725.121:806): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=19634 profile="/usr/sbin/cupsd"
[1727858.584891] type=1503 audit(1245684725.213:807): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=19634 profile="/usr/sbin/cupsd"
[1727858.584948] type=1503 audit(1245684725.213:808): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=19634 profile="/usr/sbin/cupsd"

```

Is there anyway to view the data in those database files??

Now for the strange one....I can print test pages on the printer...
:confused:

UPDATE: I can print out of open office. The file I am trying to print is a .tif file. I have printed this file before on this printer. I have tried opening it in envince and eye of gnome with the same results.
I looked at the printing window in several ubuntu apps and open office. It seems that the printing app for ubuntu is different from the one in open office.....
I can not print anything from any stock ubuntu app.

---

### Post by lsutiger on 2009-07-14
More info.

I can print from adobe acrobat also. Again it has a different printing app vs gnome.
I still can not print from any gnome application.

BUT..when I try to print from open office of acrobat, I need to open the printing console and authorise the release the document.....this is very frustrating!


UPDATE: Here is the error I get when trying to print from a gnome based app:
Failed to print document
Can't prompt for authorization

PS - Off of this topic...why do I have to restart so much after updates now?

---

### Post by lsutiger on 2009-07-17
Bump

---

### Post by lsutiger on 2009-07-26
bump

---

### Post by newagelink on 2009-08-14
I don't think bumping threads helps get an answer (as this thread seems to demonstrate). I found this thread through searching "Windows Printer via SAMBA", not through browsing message boards.

If no one responds to the thread, try asking for help and mentioning this thread in #ubuntu, do more internet searches, etc.

(Sorry, I can't help more: I'm trying to install a printer, myself.)

---

### Post by lsutiger on 2009-09-03
Well, we moved our office this past week, and suggested that my office partner let me host our printer. Guess what? Works like a charm now for both of us!

---

