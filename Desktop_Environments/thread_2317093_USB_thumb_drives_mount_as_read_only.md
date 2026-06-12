---
title: "USB thumb drives mount as read only"
date: 2016-03-13
forum: Desktop Environments
---

### Post by darren33 on 2016-03-13
I'm having a lot of trouble with USB thumb drives mounting as read only, or at least I get a "read only" error message when trying to write to them.  The strange thing is that when I look at permissions, my user is listed as the owner with read/write access, but my group is listed as "read only".  Dropping down to a terminal and using sudo to perform a copy to the drive works perfectly.

Anyway, this isn't isolated to just one or two drives but to *every* thumb drive I try to access from my system.  It's frustrating because this is one of those things that should "just work".  Is there a universal solution?

Thanks.

---

### Post by yancek on 2016-03-13
What's on the thumb drives and what is the filesystem type?  If you are putting Live CDs on the thumb drive, that is expectd behavior as they are read-only filesystems.

---

### Post by sudodus on 2016-03-13
If you are auto-mounting the drives, they *probably* mount at **/media/$USER/label**, where $USER is your user ID and label is the actual label of the pendrive (if there is a label. otherwise it is probably the UUID string).

Try if changing the ownership and permissions of the directory **/media/$USER** helps.

```
sudo chown $USER /media/$USER
sudo chmod u+rwx /media/$USER
```

Unmount or eject the pendrive, unplug it and plug it back in!

Can you write to it now?

-o-

If not, I will ask you to run some terminal window commands and post the results.

---

### Post by darren33 on 2016-03-20
Well oddly enough, the problem seems to have sorted itself out.  :confused:

I have no idea what changed, but I just plugged in some drives to test, and they're working perfectly.  Might it have something to do with the fact that I started using PCManFM as my file manager instead of Thunar?

---

### Post by sudodus on 2016-03-21
I'm glad that it works now :-)

I don't think, that the choice of file browser would make a difference. Maybe rebooting the computer would make a difference?

---

