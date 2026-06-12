---
title: "Crash boot : &quot;Target filesystem doesn't have requested /sbin/init&quot;"
date: 2015-10-19
forum: Desktop Environments
---

### Post by adikse-09 on 2015-10-19
Hi !

I have an extern HDD with Ubuntu 14.04 installed. I've updated it to 15.04 but after the reboot I had an error : "Target filesystem doesn't have requested /sbin/init."
You can see it with this screenshot :[ATTACH=CONFIG]265045[/ATTACH]

I tried to fix this by following the instructions on this website : [http://pinoy-computing-tips.blogspot.fr/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.fr/2010/08/how-to-fix-ubuntu-error-no-init-found.html)
But it didn't work, I still have the same problem.

What should I do in order to repair my partition ?

---

### Post by ian-weisser on 2015-10-21
To fix the problem, you need to understand what's going on.

During boot, GRUB tells the BIOS/EFI where to look to load the kernel and then the initramfs.
The initramfs (which includes busybox) loads from the (read-only) hard drive into RAM, then starts a proto-init process. Proto-init creates the filesystem, remounts the hard drive Read/Write, and then passes contol over to the *real* init process located on your (hard drive) filesystem at /sbin/init. Finally, the real init process starts the system you recognize.

That "passing contol over to the *real* init process" has failed, because the /sbin/init file apparently isn't there.

Use the busybox commands (like 'ls') to see if /sbin/init exists.
If not, check that GRUB is pointing to the correct partition.

---

