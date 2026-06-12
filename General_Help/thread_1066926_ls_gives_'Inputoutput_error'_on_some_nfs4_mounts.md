---
title: "ls gives 'Input/output error' on some nfs4 mounts"
date: 2009-02-11
forum: General Help
---

### Post by xdcdx on 2009-02-11
Hello,

I have been trying to configure some nfs4 mounts on a cluster, and I get some strange and pseudo-random 'Input/output error' when I perform 'ls' or 'cp -r' over some mounted directories.

On the other hand, 'cd' and 'cp' for individual files seems to work normally (haven't performed extensive testing).

I will now explain my particular setup and kernel and ubuntu versions.

I have several nodes, named 1 to 9. Node 1 shares the /home/ directory, and nodes 2 to 9 shares a /scratch-l/ directory. All nodes mount all shares: they mount n1:/home/ on /home/, and nx:/scratch-l/ on /scratch/x/.

I always get the Input/output errors when I'm lsing on /home/ or in /home/someuser/. Some ls on /scratch/x/ gave the same error, while some other didn't, but after rebooting all the nodes , all the /scratch/x/ seem to be working normally. ls on NFS4 mounted /home/ never seems to work, even after reboots. The pseude-randomness of this problem makes it very hard for me to debug.

I didn't get the 'Input/output errors' with NFS3 but, on the other hand, I got some very weird slow downs or complete hangups of nodes due to the NFS mounts, that's why I'm migrating to NFS4. With NFS4 there aren't hang ups, but there's this new problem.

I have:
- [Ubuntu-Server 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1), with all the security updates until today.

I can't readily upgrade to a newer ubuntu distribution to see if this will solve the problem because it would be too much work.

My kernel is (all the nodes are Intel 64 bit Xeons):
Linux n1 2.6.15-53-amd64-server #1 SMP Mon Jan 26 00:08:39 UTC 2009 x86_64 GNU/Linux

This is my n1 /etc/exports:
/                                       192.168.1.0/255.255.255.0(rw,sync,fsid=0)
/tftpboot/nfsroot/heura.client          192.168.1.0/255.255.255.0(rw,sync,nohide,no_root_squash)
/home                               192.168.1.0/255.255.255.0(rw,sync,nohide,no_root_squash)

And this my nx /etc/exports:
/                               192.168.6.0/255.255.255.0(rw,sync,fsid=0)
/scratch-local                  192.168.6.0/255.255.255.0(rw,sync,nohide)

These are the pertinent /etc/fstab lines for n1:
/dev/sda7       /home           ext3    defaults                      n2:/scratch-local /scratch/2 nfs4   hard,intr,rsize=32768,wsize=32768 0 0
n3:/scratch-local /scratch/2 nfs4   hard,intr,rsize=32768,wsize=32768 0 0
...

And these for n2:
n1:/home /home nfs4 hard,intr,rsize=32768,wsize=32768 0 0
n2:/scratch-local /scratch/2 nfs4   hard,intr,rsize=32768,wsize=32768 
n3:/scratch-local /scratch/2 nfs4   hard,intr,rsize=32768,wsize=32768 
...

Hope somebody can shed some light to this bug. If more info about my system is needed, tell me and I will provide it.

Thanks!

---

### Post by valentijnsessink on 2009-06-23
I can't shed any light on it, but I can confirm it with almost the same setup: 6.06 server (although 32 bit), and 8.04 clients. The clients are a mixture of nfs3 and nfs4 and the nfs4 mounts sometimes break, returning *Input/output error* on every readdir-call.
Unmounting and remounting just does not work, a server reboot seems to be required to fix things.
At different locations where we have only nfs4 mounts, things seem to be all right, but please keep in mind that our mixed nfs3/4 environment is also the largest one, so I can't be really sure that mixing these is the culprit.
Our own server runs 8.04 since last week, testing it shows no problems at all (I'm running a couple of commands that create files and directories, then another group of commands that deletes them, in the hope of recreating the problem - but alas).

---

### Post by xdcdx on 2009-06-23
valentijnsessink, thanks for the info!

The issue seems to have been fixed in kernel version 2.6.28-11-server.

---

