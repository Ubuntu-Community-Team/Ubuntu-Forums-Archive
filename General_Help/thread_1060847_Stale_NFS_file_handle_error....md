---
title: "Stale NFS file handle error..."
date: 2009-02-05
forum: General Help
---

### Post by photon_man62 on 2009-02-05
Hello. I seem to get this error message when I try to install anything from the DB:

aleksander@Aleksander-Laptop:~$ sudo apt-get install g++
[sudo] password for aleksander: 
[B]Reading package lists... Error!
E: Could not open file /var/cache/apt/pkgcache.bin - open (116 Stale NFS file handle)
E: Failed to truncate file - ftruncate (9 Bad file descriptor)
E: The package lists or status file could not be parsed or opened.[/B]
aleksander@Aleksander-Laptop:~$ 

I'm running Ubuntu 8.10.

---

### Post by photon_man62 on 2009-02-05
I found something like this:

```
Q. Why do I get the following error message sometimes?
	Stale NFS file handle

A. This type of error message is seen when a file or directory that was opened by an NFS client is removed, renamed, or replaced. 
   To fix this problem, the NFS file handles must be renegotiated. Try one of these on the client machine:
   
[B]	a) Unmount and remount the file system, may need to use the -O (overlay option) of mount.
	
	   From the man pages:
	           -O    Overlay mount.  Allow  the  file  system  to  be
	                 mounted  over  an  existing mount  point, making
	                 the underlying file system inaccessible.   If  a
	                 mount is attempted on a pre-existing mount point
	                 without setting this flag, the mount will  fail,
              		 producing the error "device busy".
              		 
	b) Kill or restart the process trying to use the nonexistent files.
	
	c) Create another mount point and access the files from the new mount point.[/B]
	
	d) Run: /etc/init.d/nfs.client stop; /etc/init.d/nfs.client start
	
	e) Reboot the client having problems.
```

I don't get the bold parts.

---

### Post by photon_man62 on 2009-02-05
I have also noticed I don't have any file called pkgcache.bin in /var/cache/apt. In fact, apt is empty.

---

### Post by photon_man62 on 2009-02-05
Hello? Can ANYONE help?

---

### Post by ridetheteapot on 2009-02-05
first backup the other bin file srcpkgcache.bin if you have it somewhere else then try just updating the apt database 'sudo apt-get update'

---

### Post by photon_man62 on 2009-02-05
> **ridetheteapot said:**
> first backup the other bin file srcpkgcache.bin if you have it somewhere else then try just updating the apt database 'sudo apt-get update'

Thanks but a few seconds ago I booted into GPartEd and checked/repaired the filesystems (/ and /home), and now everything seems to work.

---

