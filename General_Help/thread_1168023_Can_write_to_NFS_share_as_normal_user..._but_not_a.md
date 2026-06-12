---
title: "Can write to NFS share as normal user... but not as root!"
date: 2009-05-23
forum: General Help
---

### Post by Jengu on 2009-05-23
My desktop has /home setup as an NFS share. On my laptop, I'm logged in as root (recovery console). I successfully mount my desktop's share and can see files with ls. But I can't write any files! I happen to use the same username/pass on both my desktop and laptop. On the laptop, if I su to my normal username, and then try to write to files on the share, it works! As it so happens, I need to run a command as root on my laptop that will be writing to the NFS share. Thus the problem: I can only run the command I need if I'm root, but the command will only work without a permissions error if I'm not. I tried being the normal user and using sudo, but I had the same problem.

I suspect I misunderstand how NFS is supposed to work, but at this point this behavior just seems bizarre O_o Any ideas?

---

### Post by gpredrag on 2009-05-23
It is how it is supposed to work. By default, on your nfs server, file systems are exported with root_squash option, which means that root on any nfs client is mapped to user nobody on server. It is a security measure, since nfsv3 (unlike nfsv4) is pretty insecure, unless used on secured network, and tightly controlled clients. If you wish that root on client is mapped to root on server, put no_root_squash in your exports file on nfs server. Check man exports.

---

