---
title: "changing owner/permission for /windows"
date: 2004-12-17
forum: Desktop Environments
---

### Post by tuco on 2004-12-17
I tried changing the permission to my windows partition so that I can use wine as user and not root. However, everytime I change either the access or owner:group, it reverts it back to root:root having access. Any help would be great.

---

### Post by taygan on 2004-12-17
You can't chmod a vfat filesystem after it's mounted. You have to set the umask in the mount command or in /etc/fstab

See this thread:

[http://www.ubuntuforums.org/showthr...fat+permissions](http://www.ubuntuforums.org/showthr...fat+permissions)

or this thread:

[http://www.ubuntuforums.org/showthr...fat+permissions](http://www.ubuntuforums.org/showthr...fat+permissions)

or this thread:

[http://www.ubuntuforums.org/showthread.php?t=8061](http://www.ubuntuforums.org/showthread.php?t=8061)

You can add either a umask=000 and/or set yourself as the owner (gid=1000 uid=1000)

Good Luck!

---

### Post by tuco on 2004-12-20
thanks, I will give these try.

---

