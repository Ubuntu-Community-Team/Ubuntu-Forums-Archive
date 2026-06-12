---
title: "Unmounting disconnected samba share"
date: 2009-04-22
forum: General Help
---

### Post by Zer0d on 2009-04-22
Samba lost connection with the share because the other computer changed IP-Address. When I try to umount the volume now I only get the message in the image below:

----------------------------------------------------------------
[IMG]http://img90.imageshack.us/img90/152/46412395.png[/IMG]
----------------------------------------------------------------

I've tried restarting samba still not able to unmount. How do I go about this?

---

### Post by StuartN on 2009-04-22
Try umount -f

---

### Post by Zer0d on 2009-04-22
I used the GUI to mount the drive from Places -> Network -> 00xff -> Share so I'm not sure where the default mount location is for samba shares?

---

