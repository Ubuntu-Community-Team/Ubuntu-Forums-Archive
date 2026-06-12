---
title: "sudo is borked"
date: 2006-02-02
forum: Desktop Environments
---

### Post by anders.ostling on 2006-02-02
Howdy

Since I installed kwin 3.5, my sudo subsystem seems to be non-functional. Whenever I do the sudo command, I am promted for the password and then the promp returns immediately without no action or error message.

anos@zoolog:~$ sudo ps vax
Password: 
anos@zoolog:~$
anos@zoolog:~$ sudo ps vax
anos@zoolog:~$

The /etc/sudoers seems to be unaltered, and /usr/bin/sudo is still setuid

root@zoolog:/usr/bin# ls -l /etc/sudoers
-r--r-----  1 root root 406 Jan 31 09:08 /etc/sudoers

root@zoolog:/usr/bin# ls -l /usr/bin/sudo
---s--x--x  1 root root 93332 Jan  9 11:41 /usr/bin/sudo

What have I done, and more important; what can I do to restore sudo? I have tried to uninstall/re-install sudo itself but that did not help much.

Thanks

Anders

---

### Post by darth_vector on 2006-02-02
you want to check two things:

1) check /etc/hosts you should have an entry like
127.0.0.1       localhost.localdomain   localhost       machine-hostname

2) there should be an entry in /etc/sudoers like
your_username ALL = (ALL) ALL

---

### Post by astoltz on 2006-02-02
Didn't Breezy change the sudoers file from "your_username ALL = (ALL) ALL"
to "%admin ALL = (ALL) ALL"?  So that all members of the admin group can use sudo.  Anyway, make sure you are a member of the admin group: less /etc/group.

---

### Post by anders.ostling on 2006-02-03
Hi
That was it. Somehow my account name had been stripped from the admin group. I granted myself as to the admin group, and now sudo works again!

Thanks a bunch!!!
Anders

---

