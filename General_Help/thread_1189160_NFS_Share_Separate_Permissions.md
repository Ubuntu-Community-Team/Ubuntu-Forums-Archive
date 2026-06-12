---
title: "NFS Share Separate Permissions"
date: 2009-06-16
forum: General Help
---

### Post by deibertine on 2009-06-16
Hi there,

I was wondering if there's a way to create an nfs share with separate permissions per user?

userro: read only priv.
userrw: read/write priv.

This way when user "userro" mounts that share, he/she can only read but when user userrw will be able to read/write to it. 

One of the suggestions was to input the following to /etc/exports:
/sharednfs     *(ro,no_subtree_check)
/sharednfs   dev34.csaa.com(rw,no_root_squash,sync)

However when I do mount it in ro machine, im only getting some of the files within the nfs share:

total 4
0 drwxr-xr-x 2 root root    0 2009-06-15 16:20 .
4 drwxr-xr-x 6 root root 4096 2009-06-15 16:20 ..
0 --w------- 1 root root    0 2009-06-15 16:20 .add
0 --w------- 1 root root    0 2009-06-15 16:20 .del
0 --w------- 1 root root    0 2009-06-15 16:20 .export
0 -r--r--r-- 1 root root    0 2009-06-15 16:20 exports
0 -rw------- 1 root root    0 2009-06-15 16:20 filehandle
0 -rw------- 1 root root    0 2009-06-15 16:20 .getfd
0 -rw------- 1 root root    0 2009-06-15 16:20 .getfs
0 -rw-r--r-- 1 root root    0 2009-06-15 16:20 max
0 -rw------- 1 root root    0 2009-06-15 16:20 nfsv4
0 -rw------- 1 root root    0 2009-06-15 16:20 nfsv4
0 -rw------- 1 root root    0 2009-06-15 16:20 pool
0 -rw-r--r-- 1 root root    0 2009-06-15 16:20 portlist
0 --w------- 1 root root    0 2009-06-15 16:20 .svc
0 -rw------- 1 root root    0 2009-06-15 16:20 mainthreads
0 --w------- 1 root root    0 2009-06-15 16:20 .export
0 -rw------- 1 root root    0 2009-06-15 16:20 subversions


For rw machine, I'm seeing all directories I wanted in full:

4 drwxrwxr-x   8 root root 4096 Jun 11 15:49 .
8 drwxr-xr-x   7 root root 4096 Jun 15 15:59 ..
4 drwxrwxr-x   2 root root 4096 Jun 11 15:43 Vendors
4 drwxrwxr-x   2 root root 4096 Jun 11 15:44 Disclosure
4 drwxrwxr-x   3 root root 4096 Jun 11 15:44 Destination
4 drwxrwxr-x   9 root root 4096 Jun 11 15:48 Distros
4 drwxrwxr-x   2 root root 4096 Jun 11 15:49 Dropoff
4 drwxrwxr-x  30 root root 4096 Jun 11 16:28 XEntOS
 

Basically I want both of them to see all directories but ro will only have read only rights to the nfs mount. 

Any suggestions? 

Thanks!
DB :(

---

### Post by deibertine on 2009-06-17
Ok I did change the permissions to nobody (own/grp) and chmod to 777 on the nfs share.
Also added few strokes in /etc/exports: /sharednfs     *(rw,all_squash,sync,anonuid=501,anongid=501)
However doing so will grant ALL users mounting this drive r/w access to the share, is this true?

If so, how can I have one user have all RW rights and others only READ access? 

Need expert advise please.

I'd appreciate it.

Thanks! 
DB

---

