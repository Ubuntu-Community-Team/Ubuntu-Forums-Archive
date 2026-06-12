---
title: "acpid can't open socket Read Only File System"
date: 2009-01-06
forum: Desktop Environments
---

### Post by Caesonia on 2009-01-06
Hi all,

I have only been using and working on Linux about a year - and that includes CentOS 5.0 and Ubuntu. Currently I use 8.04 for internal server machines. and RHEL for external. ( Not my choice, it was in place before I was hired.)

So, I do have some decent experience, but still fit into the realm of huh?


This particualr server houses my LDAP server, and it has been running smoothly for 6 months. However, I needed to do a reboot and it won't reboot, except in safe mode.

There is something going on with the ACPID services. Initially I get a series of odd errors:

chmod: cannot access /some directory/ :No such file or directory
chown cannot access /some directory/ : No such file or directory

for a number of processes,

and then I get 

Loading ACPID modules
starting acpid services
acpid can't open socket /var/run/acpid.socket: Read Only File System..

I have seen some bugs that seem related, but I cannot run the reconfigure --a command becuase in safe mode I have Read Only permissions. 

Yes, I do know that I can unmount and remount the drive, but the last time I tried it for something else in recover mode, it seemed to have 'forgotten' the changes.

Has any one run into this? And do they know what might be missing or causing this problem?

Thanks.

---

