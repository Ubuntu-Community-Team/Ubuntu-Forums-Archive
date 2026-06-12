---
title: "Skip sudo password for one command only"
date: 2012-02-22
forum: Desktop Environments
---

### Post by lucacerone on 2012-02-22
Dear all,
on my laptop I often unmount portable devices issuing
```
 
sudo umount /path/to/device

```
from the terminal.

I'd like to know if there is a way to make sudo asking no password when my user (but no others) want to unmount certain specific devices. 

In principle it should be possible because unmounting it from Nautilus asks for no password.

I guess that maybe modifying the fstab could avoid making me use sudo at all, but I don't know
how (so if you know, that would be useful as well).

I though wonder if there is a way to make only certain commands passwordless for specific users
using sudo.

Thanks a lot for your help,
Cheers, Luca

---

### Post by Lars Noodén on 2012-02-22
To do it with sudo, it should be something like this:

```

%lucacerone ALL=(ALL) NOPASSWD: /bin/umount /path/to/device

```

See the documentation for [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html) for details. 

Or if you use [fstab](http://manpages.ubuntu.com/manpages/oneiric/en/man5/fstab.5.html) you can add 'user' to the fourth field and it should allow the user to mount and unmount.

---

