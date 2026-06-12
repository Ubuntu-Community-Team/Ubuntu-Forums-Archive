---
title: "vmware file transfer speed between guest and host operating system"
date: 2006-12-01
forum: Desktop Environments
---

### Post by quickk on 2006-12-01
Hi everyone, 

   I finally got vmware setup on my edgy machine.  For the longest time, I didn't understand how to transfer files back and forth between host and guest operating systems.  I finally figured out that you need samba to do so.  Using a very rudimentary samba smb.conf file:

```


[global]
workgroup = VIRTUAL
netbios name = SACAPUS

[homes]
comment = Home Directories
create mode = 0600
directory mode = 0755
valid users = %S
read only = No
browseable = No


```

I can have full access to my ubuntu home directory from within the guest winXP operating system.  It's just that transferring files back and forth seems slow.  I've made some tests with a 350 MB file, and the transfer rate is 5MB/s.  Is this normal?  

Is there any way to make the data go back and forth between operating systems in the same way that I would copy one file to another within the same operating system?  Is seems ridiculous that I'd have to send the file to my router, and then back to the same machine, instead of just having the hard drive directly copy the file to a new location.  

Any insight would be greatly appreciated.  Thanks!

---

### Post by schport on 2006-12-03
I am having the same issue with the extremely slow file transfer speeds between the host and guest systems.

It would be nice to find out a way to resolve this without having to transfer files to a 3rd computer first.

---

### Post by quickk on 2006-12-04
What would really help is if someone told us what kind of file transfer speeds are normal...

---

### Post by schport on 2006-12-04
normally I can transfer a 350MB file in about 3 minutes which is about 2MB a second.  Between the vmware host and guest, that same file takes about 3 hours to transfer, which is about 30KB a second.

---

### Post by quickk on 2006-12-05
schport, that's terrible!  I guess that I shouldn't complain with my 5 MB/s that I get between the vmware host and guest.  I wish that I could help you, but I really don't know anything about this stuff ](*,) .

It would be great if there was some way of getting the vmware guest to natively "see" the host's file system without resorting to networking.  It really seems like a prodigious waste of bandwith to transfer files across the network when they are actually just going to a different location on the same physical drive that they started on.

---

