---
title: "automount usb not working"
date: 2006-10-05
forum: Desktop Environments
---

### Post by gdlx on 2006-10-05
Dapper no longer recognizes the flash drive when it is plugged in or cdrom when inserted into drive.  The usb mouse still works. It has been two days since this occurred.

I have tried to run pmount from cl but it says I don't have permission.

Anyone???

](*,)

---

### Post by someguyouknow on 2006-10-05
I think it may have been one of the recent updates...
i have a similar problem with my digital camera...
i would say try the next kernel to see if it works...

---

### Post by gdlx on 2006-10-09
Tried an older kernel but no help.
The CD also doesn't mount properly and displays the same error message.  However, it is still possible to access the CD and retrieve data.

Would it help to reconfigure the X-server?  I don't know enough about Linux to even get started on this problem.
:confused:

---

### Post by gdlx on 2006-10-09
My login had been removed from plugdev group.  I replaced it and everything works.  :oops: 

Another lesson learned the hard way

---

