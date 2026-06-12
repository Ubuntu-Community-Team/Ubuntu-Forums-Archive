---
title: "Trouble With Upgrade to 8.10"
date: 2009-01-07
forum: General Help
---

### Post by cheese113 on 2009-01-07
I've recently upgraded from a working version of Ubuntu 8.04 to 8.10.  After installing and restarting what I think was a successful upgrade, it won't start up on its own.  I very briefly see a message 'Unable to load system description tables' or something similar, it appears to start up as normal, and then freezes on a screen after it looks like it should have completed.  Then it doesn't respond to any mouse movement or keystroke entry.  I am able to start it by hitting esc while grub is loading and going in to recovery mode and resume normal boot.  I tried looking at the boot log, but must have turned it on incorrectly because it says nothing written.

Can someone point me to what I need to fix, a way to troubleshoot this, or anything helpful?

Thanks

---

### Post by cmnorton on 2009-01-07
This appears to be ACPI-related and might possibly require that you modify your boot parameters. I would look on Ubuntu Launchpad. You can start with these links, even though some of them are older. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258047](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258047)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280631)
[http://ubuntuforums.org/showthread.php?t=639968](http://ubuntuforums.org/showthread.php?t=639968)

---

