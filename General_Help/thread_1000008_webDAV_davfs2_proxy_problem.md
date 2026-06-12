---
title: "webDAV davfs2 proxy problem"
date: 2008-12-02
forum: General Help
---

### Post by baabakarissa on 2008-12-02
I recently upgraded from Kubuntu 7.10 to 8.10. I had used davfs2 to mount a webDAV share with no problems. I have a proxy server and it set up just fine in 7.10. Now with 8.10, having edited all the config files as they were before, davfs2 will not mount the share. I get a long dump (memory dump? backtrace?) instead. Has anyone else had a problem using a proxy with davfs2 in 8.10? Is there a system bug that is causing the memory dump?

I'll copy in the first part of what I get:

glc@Laptop:/etc/davfs2$ mount /home/glc/Operations
Please enter the username to authenticate with server         
[https://work.****.org/shared/Operations](https://work.****.org/shared/Operations) or hit enter for none.
Username: ********                                          
Please enter the password to authenticate user ****** with server
[https://work.*****.org/shared/Operations](https://work.*****.org/shared/Operations) or hit enter for none.       
Password:                                                            
*** glibc detected *** /sbin/mount.davfs: double free or corruption (fasttop): 0x08fba2c8 ***
======= Backtrace: =========                                                                 
/lib/tls/i686/cmov/libc.so.6[0xb7e9a3f4]                                                     
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7e9c456]                                         
/sbin/mount.davfs[0x80594cd]                                                                 
/sbin/mount.davfs[0x805ecdc]                                                                 
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7e41685]                             
/sbin/mount.davfs[0x804b5d1]                                                                 
======= Memory map: ========                                                                 
08048000-08067000 r-xp 00000000 08:02 155319     /usr/sbin/mount.davfs                       
08067000-08068000 r--p 0001e000 08:02 155319     /usr/sbin/mount.davfs                       
08068000-08069000 rw-p 0001f000 08:02 155319     /usr/sbin/mount.davfs

---

### Post by baabakarissa on 2008-12-05
BTW, I can connect to the webDAV folder through the proxy in Konqueror, so the problem is with davfs2. Would love to be able to use davfs2 because the set up is so nice once you're connected. Any thoughts?

---

### Post by baabakarissa on 2009-01-16
Now davfs2 is working. Not sure what changed. I did install a new hard drive and reinstalled everything, set it up again and it worked. Might have been my own negligence in forgetting something, might be that davfs2 has been updated or something essential changed in Ubuntu. Glad to have it working again!

---

