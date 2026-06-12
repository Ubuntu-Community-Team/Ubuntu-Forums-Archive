---
title: "NFS: worked in 5.10, not in 6.06"
date: 2006-07-23
forum: Desktop Environments
---

### Post by hobie on 2006-07-23
I have a Win32 machine running SOSSNT, which is a simple NFS server (I can't share this machine's drives from Windows because there is a necessary service that won't start).  Anyways,I successfully read its drive for months using SOSSNT and Kubuntu 5.10 by mounting with 
> sudo mount 10.0.0.6:/d ~/milo.
Since reformatting the Linux machine with 6.06, the same command gives me:
> mount to NFS server '10.0.0.6' failed: server is down.
Nothing has changed on the Win32 machine, and the SOSSNT service is running.
Has something been removed from 6.06 that was in the previous distribution?  
I read some posts saying I need portmap, which I don't have nor do any repositories I know of have it.  Is this required?

---

### Post by scxtt on 2006-07-23
try installing *nfs-common*:
[indent]sudo aptitude install nfs-common[/indent]

---

### Post by hobie on 2006-07-24
Thanks for replying. I was able to install nfs-commonn and portmap. So, I can see this:
> hobie@opus:~$ rpcinfo -p opus
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    606  status
    100024    1   tcp    609  status

This is shorter than the lists I see in other posts, which include nfs, mountd and others.
I still get the 'Server is down' message, but I can do this:
> hobie@opus:~$ showmount -e milo
Export list for milo:
/d (everyone)

This makes me think the server is ok.
Following another example, I tried:
> hobie@opus:~$ sudo mount -o nfsvers=3,udp milo:/d ~/milo
mount to NFS server 'milo' failed: possible invalid protocol.

So that's not the answer.  Do I need to install more stuff?

---

### Post by scxtt on 2006-07-24
did you try using the IP address and not "milo" (or is milo defined in /etc/hosts)?

the nfs connection from a client should work by default, but nfs-common + nfs-kernel should be all that's necessary on the nfs host ... that's all i need to do for an NFS share by xubuntu (VM) and ubuntu (host) ...

---

### Post by hobie on 2006-07-25
Hi,
Yes, milo is in /etc/hosts.
I went and installed nfs-user-server and got the missing processes, so the list is now full.
> hobie@opus:~$ rpcinfo -p opus
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    606  status
    100024    1   tcp    609  status
    100003    2   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100005    1   udp    735  mountd
    100005    2   udp    735  mountd
    100005    1   tcp    738  mountd
    100005    2   tcp    738  mountd

I tried this:
> hobie@opus:~$ nfsstat
Warning: No Client Stats (/proc/net/rpc/nfs: No such file or directory).

so I guess I am missing some files.  I also tried:
> hobie@opus:~$ cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   sockfs
nodev   securityfs
nodev   pipefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   eventpollfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   mqueue
nodev   usbfs
        ext3
        ext2

and I don't see nfs in there. Should I?

---

### Post by scxtt on 2006-07-25
i use the kernel server for nfs, don't know if that'd make a difference for you ...  but i do have "nodev nfsd" in the output for **cat /proc/filesystems** ... **nfsstat** also provides output ...
[html]:> nfsstat
Server rpc stats:
calls      badcalls   badauth    badclnt    xdrcall
0          0          0          0          0
Server nfs v2:
null       getattr    setattr    root       lookup     readlink
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
read       wrcache    write      create     remove     rename
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
link       symlink    mkdir      rmdir      readdir    fsstat
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%

Server nfs v3:
null       getattr    setattr    lookup     access     readlink
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
read       write      create     mkdir      symlink    mknod
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
remove     rmdir      rename     link       readdir    readdirplus
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
fsstat     fsinfo     pathconf   commit
0       0% 0       0% 0       0% 0       0%[/html][html]:> cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   sockfs
nodev   securityfs
nodev   pipefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   eventpollfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   mqueue
        ext3
nodev   rpc_pipefs
nodev   nfsd[/html][html]:> rpcinfo -p $HOST
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32768  nlockmgr
    100021    3   udp  32768  nlockmgr
    100021    4   udp  32768  nlockmgr
    100021    1   tcp  48517  nlockmgr
    100021    3   tcp  48517  nlockmgr
    100021    4   tcp  48517  nlockmgr
    100005    1   udp    699  mountd
    100005    1   tcp    702  mountd
    100005    2   udp    699  mountd
    100005    2   tcp    702  mountd
    100024    1   udp    805  status
    100024    1   tcp    808  status[/html]

---

### Post by hobie on 2006-07-26
Thanks again for your efforts.  
I now have it working (I think; haven't had time to test it much).  I removed SOSSNT from the Win32 machine and configured Cygwin NFS instead, following these instructions: [http://www.csparks.com/CygwinNFS/index.xhtml]("http://www.csparks.com/CygwinNFS/index.xhtml")
I didn't have to use the nfsvers=2 option as this page suggests.

---

