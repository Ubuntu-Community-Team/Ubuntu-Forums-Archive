---
title: "Problem with displaying mounted windows-dfs-share with included remote-mount"
date: 2010-12-06
forum: Desktop Environments
---

### Post by Cheveyo on 2010-12-06
Hello,
 
I'm not sure if this is the right place to put this posting, but I have to start somewhere as I'm not sure where exactly the problem lies..
 
 
**OS:** *Ubuntu 10.04 desktop, 32-bit, which is up to date*
 
 
At the office we have a windows-dfs-share, let's call it "DFS-SHARE". Within this "DFS-SHARE" lies a folder, which in itself is a mounted share from another system outside of the dfs. Let's call it "REMOTE-MOUNT.
 
I am mounting the "DFS-SHARE" to "MOUNTPOINT" with the following little script:
 
```
mount.cifs //domain/dfs/DFS-SHARE /home/user/MOUNTPOINT -o user=XXX,password=YYY,iocharset=utf8,codepage=cp850
 

```
My problem is that upon mounting the share, the system not only automatically creates a link on my desktop named "MOUNTPOINT", which points the mounted share, but also creates a second link called "REMOTE-SHARE", which exactly points to that other system, even though my mountscript does not mount it at all.
 
It is this mechanic of displaying/ automounting that second, remote share that I need to get rid off. When I check my mounted filesystems, this REMOTE-SHARE is not listed as mounted, allthough the link on the desktop is working.
I suspect that this effect might be caused by Nautilus, but I am not sure here or how to turn that off.
 
It is my hope, that someone here will be able to point me into the right direction.
 
Sincerly
 
Cheveyo

---

