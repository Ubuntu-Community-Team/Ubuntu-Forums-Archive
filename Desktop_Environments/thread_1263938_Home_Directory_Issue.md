---
title: "Home Directory Issue"
date: 2009-09-11
forum: Desktop Environments
---

### Post by sirius1 on 2009-09-11
8.04.1

I was messing with Gnome permissions.

When I type the followiong commnd from my home directory, larry@apollo:~$
I get the wrong directory.

$ cat /etc/passwd
returns:

root:x:0:0:root:/root/home/iris/bin/bash
daemon:x:1:1:daemon:usr/sbin:/bin/bash
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh


iris is even another non privileged account.

Thanks for any guidance,
Larry

---

### Post by sirius1 on 2009-09-11
I found the following to add to the list:

$df -h

/dev/sda2         Use 100%
gvfs-fuse-daemon  Use% 100%  

My root volume appears to be full.

---

### Post by sirius1 on 2009-09-26
$ sudo find / -type d -name *Trash*

Which found all trash files, then I deleted the Trash.

Had one permission issue to resolve with one path.

Emptying trash resolved disk space issue.

---

