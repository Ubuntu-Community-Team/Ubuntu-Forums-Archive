---
title: "a Linux 101 question"
date: 2009-01-11
forum: Desktop Environments
---

### Post by yosepht on 2009-01-11
I see some executable files in my /usr/bin/ directory that are
highlighted in red. What does it mean? ):P

---

### Post by mcduck on 2009-01-11
If you run "ls -l /usr/bin", you'll notice the difference in those file's permissions. "sudo" is one of the binaries marked in red, and it's permissions are "-rw**s**r-xr-x".

The "s" there is SUID, as in "set user ID". This means that the file executes with the same permissions the file's owner has (instead of using the permissions of the user who executed the file, like usually).

This means that if the executable file is owned by root, the program will run with root permissions even when started by normal user. (of course the user must still have the right to execute the file in the first place..)

edit: you can find better explanations for SUID, SGID and Sticky bits here: [http://www.zzee.com/solutions/linux-permissions.shtml#setuid]("http://www.zzee.com/solutions/linux-permissions.shtml#setuid")

---

### Post by yosepht on 2009-01-11
Got it. Thanks for the great explanation.

---

