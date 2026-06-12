---
title: "permissions for Desktop shortcuts"
date: 2009-07-13
forum: Desktop Environments
---

### Post by nucleuskore on 2009-07-13
Hi everyone
I wanted to create a shortcut to my Windows partitions on my Ubuntu Desktop. So I opened a terminal and typed

[B]ln -s /windows/c/ /home/neville/Desktop/C
ln -s /windows/d/ /home/neville/Desktop/D[/B]

and got the shortcuts. I then tried to create shortcuts which cannot be deleted by me unless I'm root. So I deleted the above shortcuts and gave

[B]sudo ln -s /windows/c/ /home/neville/Desktop/C
sudo ln -s /windows/d/ /home/neville/Desktop/D[/B]

However I am able to delete these very easily. When I tried to see the ownership I see it's owned by root, and **sudo getfacl Desktop/C** gives me the following

# file: Desktop/C
# owner: root
# group: plugdev
user::rwx
group::rwx
other::---

**groups neville** gives me this
neville adm dialout cdrom plugdev lpadmin admin sambashare vboxusers

Any suggestions?

---

