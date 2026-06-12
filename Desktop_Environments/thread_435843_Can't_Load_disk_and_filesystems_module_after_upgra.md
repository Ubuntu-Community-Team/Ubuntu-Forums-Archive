---
title: "Can't Load disk and filesystems module after upgrading to fiesty"
date: 2007-05-07
forum: Desktop Environments
---

### Post by uhlive on 2007-05-07
I've read that this only happens when you have more then one harddrive.. which is my case..

But has there been a fix yet?

---

### Post by uhlive on 2007-05-07
Any help guys?

---

### Post by visionary on 2008-02-26
Ok this is a solution i applied.....

[B]
I guess most of us would have encountered this error after we try to apply some ubuntu tweaks to speed up the systems.[/B]

To reset do this..

**1)back up /etc/fstab**
[B]
2)sudo gedit /etc/fstab (GNOME USERS) or sudo kate /etc/fstab (For KDE users)
[/B]
**3)Look for a line which looks like this**

defaults, errors =remount-ro,data=writeback,noatime 0

Now **we need to remove WRITEBACK and NO TIME entries**.So delete those two words only.
Make sure the line now looks something like this

nouser,defaults,errors=remount-ro,atime,auto

I am NOT saying u copy my line above, instead asking you to remove WRITEBACK and NO TIME entries from the line found in your system.

Now save the file.
Go back to KCONTROL and back into disk & file system. Hopefully that would have resolved your issue.

Good luck pal.


:)

---

