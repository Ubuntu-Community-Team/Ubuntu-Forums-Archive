---
title: "Force a file system error on Ext3?"
date: 2011-04-06
forum: Desktop Environments
---

### Post by Jack_Simth on 2011-04-06
This is probably going to seem a strange question, but I need a way to force a file system error on an extension-3 partition, so I can verify machine behavior during a common type of failure event I see at work.  

Yes, I know how to force it to check file system integrity on reboot (shutdown -rF now).  Yes, I know how to scan the disk (umount [partition in question] followed by e2fsck [partition in question]).    However, if these changes to the box work out, it's going to be a mostly-automated system where getting someone on-location to type out 'e2fsck' is (while possible) not desirable.  So I'm paring the system down, getting the higher-failure sections in partitions not mounted in /etc/fstab, and instead mounting them in the middle of the init-v boot up (just before the stuff that requires those partitions), so that if the higher-failure sections (higher failure due to traffic to and from the device) have a file system error, it'll still come up enough for me to get into it remotely to run e2fsck from my office.  

But before I put this out in the field, I need a way to make it have a problem on-demand.  Something e2fsck will be able to correct without guidance beyond the -y flag, but something that would cause the mount command to say 'this is a damaged file system' by whatever phrasing.  Does that make sense?

---

