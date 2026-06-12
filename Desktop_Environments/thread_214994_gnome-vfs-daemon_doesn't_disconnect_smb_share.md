---
title: "gnome-vfs-daemon doesn't disconnect smb share"
date: 2006-07-13
forum: Desktop Environments
---

### Post by dseomn on 2006-07-13
Sorry for the cross post from [http://ubuntuforums.org/showthread.php?t=210306]("http://ubuntuforums.org/showthread.php?t=210306"), but I downgraded to 6.06 (with the same problem) and I still haven't gotten a response there.

> When I connect to a windows share (Places -> Connect to Server), use the share, and then right click on the share and select Unmount Volume, ubuntu doesn't actually disconnect from the share. When I connect again, it doesn't ask me for the password and after I unmount the share again, netstat and the server logs both show that gnome-vfs-daemon is still connected to the server.

How can I get gnome-vfs-daemon to disconnect from the server?

If it doesn't disconnect, the server doesn't run the postexec command (umount), so I can't eject the disk without ssh'ing to manually unmount it.

> gnome-vfs-daemon seems to disconnect after a timeout or something. The server log is:
```
[2006/07/06 13:46:19, 1] smbd/service.c:make_connection_snum(642)
  helicon (192.168.1.11) connect to service 5.25 inch Floppy Drive initially as user files (uid=1001, gid=1001) (pid 2325)
[2006/07/06 14:24:54, 1] smbd/service.c:close_cnum(830)
  helicon (192.168.1.11) closed connection to service 5.25 inch Floppy Drive
```
it looks like the timeout might be 30min after the last activity

---

