---
title: "Permission to Use HDD?"
date: 2009-01-08
forum: General Help
---

### Post by Starclopsofish on 2009-01-08
Sorry if this has been answered before, I searched and couldn't find anything.

I just installed Intrepid on my new build and I'm loving it so far. However when I try to use any hard disk other than the one the OS was installed on, I get a message telling me that system policy prevents this.

I've tried starting Nautilus with sudo and modifying the permissions, but to no avail... any suggestions?

---

### Post by mssever on 2009-01-08
That is almost certainly a permissions problem, and should be easy to fix. However, I need more information before I can help you.


[LIST=1]
[*]What is the exact error message you get?
[*]What kind of filesystem is on the disks (e.g., ext3, NTFS, etc.)?
[*]Are the disks in question internal or external?
[*]What are the contents of /etc/fstab?
[/LIST]

EDIT: In the future, you can save time by always including the exact text of any error messages whenever you ask for help. Even if you don't understand them, the person who can help you probably does.

---

### Post by jerome1232 on 2009-01-08
What filesystem's are the drives using? Non-linux filesystems don't support unix style permissions (so chown/chmoding them won't work) so you have to mount them with certain options to set permissions.

This is a good read for learning more about that.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Starclopsofish on 2009-01-09
Thanks for your quick responses!

Strangely, it works now. I suppose it just needed a few reboots. Weird, because I rebooted before...

Anyway, I'm just happy it's working! Time to start ripping my music library :popcorn:

---

