---
title: "NFS - cant' connect port 32770"
date: 2009-01-09
forum: General Help
---

### Post by comforteagle on 2009-01-09
Update: there's no service running on that port.  Shoulnd't there be for NFS?

----
I'm trying to set up nfs bwtween two intrepid machines.

when trying to mount:
mount ip:/mnt/testing /mnt/testing I just get a timed out msg, retrying msg, then finally giving up.

trying to telnet to the server machine from the client I can on port 111, 2049, but not 32770.
32770 isn't denied, but "telnet: Unable to connect to remote host: Connection timed out"

I suspect herein lies my problem, as the firewall is complete off.

rpcinfo -p shows:
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  55095  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  46722  nlockmgr
    100021    3   tcp  46722  nlockmgr
    100021    4   tcp  46722  nlockmgr
    100005    1   udp  32771  mountd
    100005    1   tcp  46489  mountd
    100005    2   udp  32771  mountd
    100005    2   tcp  46489  mountd
    100005    3   udp  32771  mountd
    100005    3   tcp  46489  mountd


Can anyone help with this? I've googled my brains out regarding how to properly setup nfs on ubuntu & this is the first thing that makes sense, having tried everything else.

---

### Post by jgoguen on 2009-01-10
Did you see the documentation at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) yet?  I haven't tried it myself, but it looks good.

---

### Post by albinootje on 2009-01-10
> **comforteagle said:**
> 
I'm trying to set up nfs bwtween two intrepid machines.

when trying to mount:
mount ip:/mnt/testing /mnt/testing I just get a timed out msg, retrying msg, then finally giving up.

trying to telnet to the server machine from the client I can on port 111, 2049, but not 32770.
32770 isn't denied, but "telnet: Unable to connect to remote host: Connection timed out"


Can you post a version of your /etc/exports ?
Are you using the kernel- or userland NFS server ?
Where did you get the 32770 port information from ?
```

$ grep 32770 /etc/services 
$

```

---

### Post by comforteagle on 2009-01-10
> **jgoguen said:**
> Did you see the documentation at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) yet?  I haven't tried it myself, but it looks good.

I have. It indeed looks very good.  Which, is why I'm so stumped.

---

### Post by comforteagle on 2009-01-10
> **albinootje said:**
> Can you post a version of your /etc/exports ?
Are you using the kernel- or userland NFS server ?
Where did you get the 32770 port information from ?
```

$ grep 32770 /etc/services 
$

```

/etc/exports:
```
/mnt/testing *(rw,sync,no_root_squash,no_subtree_check)

```
I've tried using the correct internal network ip as well & tried various combinations of the options... root_squash, async, subtree_check etc., run exportfs -a & restarted services.

I'm using nfs-kernel-server

I got the 32770 from this tutorial:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

I see now it says 32771, but I was checking ports & saw 32770 at the time of writting.  I've read that portmap does some random port assignments so I'm thinking this may be a red herring at this point.

---

### Post by albinootje on 2009-01-10
> **comforteagle said:**
> 
I see now it says 32771, but I was checking ports & saw 32770 at the time of writting.  I've read that portmap does some random port assignments so I'm thinking this may be a red herring at this point.

I think the ports 32771 or 32770 are certainly not the bottleneck in the setup.

FWIW :
# my /etc/exports on my local file server
/home/ftp	172.19.3.0/255.255.255.0(rw,sync,subtree_check)

Did you check logfiles on both machines ?
Did you not forget to restart the nfs-server after each change in /etc/exports ?

And is /mnt/testing a mounted device ?
Can you try with exporting /mnt instead ?

---

### Post by comforteagle on 2009-01-10
> **albinootje said:**
> I think the ports 32771 or 32770 are certainly not the bottleneck in the setup.

FWIW :
# my /etc/exports on my local file server
/home/ftp	172.19.3.0/255.255.255.0(rw,sync,subtree_check)

Did you check logfiles on both machines ?
Did you not forget to restart the nfs-server after each change in /etc/exports ?

And is /mnt/testing a mounted device ?
Can you try with exporting /mnt instead ?

logfile: /var/logs/messages says:
```
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: nfsd: last server has exited
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: nfsd: unexporting all filesystems
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: **RPC: failed to contact portmap (errno -5**).
Jan 10 15:29:56 domU-12-31-38-00-5C-11 kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 10 15:29:56 domU-12-31-38-00-5C-11 kernel: NFSD: starting 90-second grace period
Jan 10 15:30:06 domU-12-31-38-00-5C-11 portmap: Removing stale lockfile for pid 17917

```

Interesting! RPC & portmap not getting along.

I tried it all over with using /mnt, exportfs -a, restated services, but got the same thing: timed out, failed.

---

### Post by albinootje on 2009-01-10
> **comforteagle said:**
> logfile: /var/logs/messages says:
```
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: nfsd: last server has exited
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: nfsd: unexporting all filesystems
Jan 10 15:29:55 domU-12-31-38-00-5C-11 kernel: **RPC: failed to contact portmap (errno -5**).

```

Interesting! RPC & portmap not getting along.

I tried it all over with using /mnt, exportfs -a, restated services, but got the same thing: timed out, failed.

You wrote that you're using 8.10 on both machines, have no firewall software running.
Is portmap running on both machines ?

I think Ubuntu 5.x had portmapper installed but listening to 127.0.0.1 only in /etc/default/portmap

With 8.x portmap should be working fine over the local network by default.

===========

By the way, you're using Xen it looks like.
Did you search for Xen + NFS specific problems already ?

I'm using OpenVZ at work, and it took me quite a while before I found out that the default virtual ethernet device in OpenVZ does not do the network broadcasting which is needed for clients "joining a MS-Windows domain" with Samba.
(I had to use the alternative virtual network device from OpenVZ)
Just as an example to show where things can go wrong ;-)

---

### Post by comforteagle on 2009-01-11
Got it working!

I added "255.255..." to exports & added a host name, in addition to IP, to /etc/hosts.

Then it worked like a charm.

For curiousity's sake I restarted the nfs-kernel-server, & portmap services to look for the rpc error, but it's gone too.  I don't know why the above would fix that, but it works so I won't question it too much more.

Thanks for your help every one.

Now to figure out the problems of  why my script, which writes to the nfs share, freezes up when outputing to that share, but not locally....

---

### Post by albinootje on 2009-01-11
> **comforteagle said:**
>  Now to figure out the problems of  why my script, which writes to the nfs share, freezes up when outputing to that share, but not locally....

If you want help for that from the forum users, start a new thread, and mark this one as SOLVED. Thanks.

---

### Post by comforteagle on 2009-01-11
I spoke too soon.

This morning I can't mount nfs; the client simply times out again.  The only change, I think, was that I changed /etc/export to change the directory to mount.  I also did change the mount instructions to the new directory.

I've chmod'd 777 the new directory too.

Alas, I'm back where I started:
```
Jan 11 15:48:01 domU-12-31-38-00-5C-11 kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 11 15:48:01 domU-12-31-38-00-5C-11 kernel: NFSD: starting 90-second grace period
Jan 11 15:48:17 domU-12-31-38-00-5C-11 portmap: Removing stale lockfile for pid 4832
Jan 11 15:48:20 domU-12-31-38-00-5C-11 kernel: nfsd: last server has exited
Jan 11 15:48:20 domU-12-31-38-00-5C-11 kernel: nfsd: unexporting all filesystems
Jan 11 15:48:20 domU-12-31-38-00-5C-11 kernel: RPC: failed to contact portmap (errno -5).
Jan 11 15:48:21 domU-12-31-38-00-5C-11 kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 11 15:48:21 domU-12-31-38-00-5C-11 kernel: NFSD: starting 90-second grace period
Jan 11 15:48:27 domU-12-31-38-00-5C-11 portmap: Removing stale lockfile for pid 5327
Jan 11 15:48:30 domU-12-31-38-00-5C-11 kernel: nfsd: last server has exited
Jan 11 15:48:30 domU-12-31-38-00-5C-11 kernel: nfsd: unexporting all filesystems
Jan 11 15:48:30 domU-12-31-38-00-5C-11 kernel: RPC: failed to contact portmap (errno -5).
Jan 11 15:48:31 domU-12-31-38-00-5C-11 kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 11 15:48:31 domU-12-31-38-00-5C-11 kernel: NFSD: starting 90-second grace period

```

If after running exportfs -a, should I see the directory in some other file?  Just to check it's being exported correctly???

If I shutdown nfs-kernel-server or portmap the client is simply refused so something is working.

---

### Post by albinootje on 2009-01-11
> **comforteagle said:**
> 
If after running exportfs -a, should I see the directory in some other file?  Just to check it's being exported correctly???


A simple 
```

exportfs

```
should show you output.

Hmmm. I just noticed that the exportfs command seems to be only included in the nfs-kernel-server and not in the nfs-user-server package.

---

### Post by comforteagle on 2009-01-11
exportfs
/mnt/testing  	10.252.174.175

looks fine to me.

Still stumped.

---

### Post by albinootje on 2009-01-11
> **comforteagle said:**
> exportfs
/mnt/testing  	10.252.174.175

looks fine to me.

Still stumped.

Read this, might help :
[http://www.nabble.com/Xen-guest-nfs-client-not-responding-td15214930.html](http://www.nabble.com/Xen-guest-nfs-client-not-responding-td15214930.html)

---

