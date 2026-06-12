---
title: "Sudo not allowed"
date: 2012-04-16
forum: Desktop Environments
---

### Post by LeeM on 2012-04-16
Hi! I'm running 11.10 on a desktop. Suddenly, sudo isn't working. I don't remember doing anything strange (?) When I try to issue a sudo command, I get the response 
[INDENT]"lee is not in the sudoers file.  This incident will be reported.
l" 
[/INDENT](lee is my user name). I tried the fixes suggested by psychocat (can't remember the thread it was in.) I re-booted into recovery mode and first, listed ;etc/sudoers. It looks ok. Right permission too (0440). Then I tried adding my username to from the admin group (psychocat suggests this). When I issue the command 
adduser lee admin
I get the following response.
[INDENT]Adding user 'lee to group 'admin'...
Adding user lee to groujp admin
gpasswd: cannot lock 'etc'group; try again later
adduser: /usr/bin/gpasswd -a lee admin   returned error code 1  Exiting
[/INDENT]
And I still can't use sudo when I reboot. Any idea what might be wrong????
Thanks!

---

### Post by papibe on 2012-04-16
Hi LeeM.

My guess is that the root filesystem was mounted as read only. While in recovery more run this before the 'adduser' command:
```
mount -rw -o remount /
```
I hope that help, and tell us how it goes.
Regards.

---

