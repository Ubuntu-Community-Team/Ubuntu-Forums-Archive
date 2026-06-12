---
title: "Can't boot: SRST failed (errno=-16)"
date: 2009-02-12
forum: General Help
---

### Post by miromiro on 2009-02-12
I have been running 8.10 for 3-4 months now, on a RAID 1 array, with no problems.

Today, I tried to boot up and it failed, with the following message:

ata4: SRST Failed (errno=-16)

it then drops into shell and says "can't detect /dev/md0"

I have been googling and searching the forums, but have been unable to locate anything that would help diagnose or fix this problem.

I am relatively new to linux and would really appreciate some help with this...

Thanks

---

### Post by mttman on 2009-02-12
try removing one of the drives and booting, then try removing the other drive and booting. if one works and the other doesn't, the one that didn't work is broken and running in raid 1 has paid off. else theres other problems, possibly data corruption. how far into boot do you get?

---

### Post by miromiro on 2009-02-12
Thanks mttman: just past the splash screen, and then it goes to custard.

I'll try removing drives and see how I go.

UPDATE: removing the drives had no effect. Failed to boot from either...

---

### Post by mttman on 2009-02-13
if the whole drive swaping thing doesn't work it's possible there's been some type of data corruption to the operating system/X window system. are you able to get to a terminal with alt-F1? what were you doing before this started? can you boot up with the backup kernel in grub?

---

### Post by miromiro on 2009-02-13
Corruption to X could be an issue: one thing I have noticed (& happened right before the failure) was that often when trying to switch between users the system would hang & I would have to hard reboot.

I can only get to a shell after the boot fails (alt + F1 doesn't work, if that is not the same thing).

Not sure how to boot from backup kernel (have done a quick google but haven't found an obvious answer yet - I'll keep looking).

Thanks for the help.

---

### Post by miromiro on 2009-02-13
I don't think it is corrupt data, as I was able to boot with a Slax live cd and could mount /dev/md0 and /dev/md2 and copy all my data to an external drive.

At this stage, I am looking at a full reinstall - but would really appreciate any insights into what happened and why...

Any ideas?

---

### Post by ilioscio on 2009-02-14
It appears to be a confirmed bug.

[[COLOR="Navy"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706")

And as usual check to make sure your bios is updated :)

---

### Post by miromiro on 2009-02-14
Thanks Ilioscio. Not sure what that means: do I have to reinstall? I can't see an obvious fix in there...

---

### Post by ilioscio on 2009-02-14
Well in that thread some seem to have success turning their drives to cable select and re-plugging in the cables. Not that that's an easy fix.. if I were you I would backup my data and reinstall :P

---

