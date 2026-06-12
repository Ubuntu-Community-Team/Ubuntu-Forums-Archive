---
title: "NFS lines in fstab aren't mounted at bootup in Jaunty"
date: 2009-06-24
forum: General Help
---

### Post by ajmcello on 2009-06-24
Here's my config. Any ideas?



10.0.1.35:/dc1/p1/web /nfs/fsp1/web nfs4 rw,rsize=8192,wsize=8192,timeo=14,intr,sec=sys,bg,ac,_netdev,auto
10.0.1.35:/dc1/stagep1 /nfs/fsp1/stagep1 nfs4 rw,rsize=8192,wsize=8192,timeo=14,intr,sec=sys,bg,ac,_netdev,auto
10.0.1.35:/dc1/mx1 /nfs/fsp1/mx1 nfs4 rw,rsize=8192,wsize=8192,timeo=14,intr,sec=sys,bg,ac,_netdev,auto

mount -a works fine.

# more nfs-common
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
# Should rpc.statd listen on a specific port? This is especially useful
# when you have a port-based firewall. To use a fixed port, set this
# this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
# For more information, see rpc.statd(8) or [http://wiki.debian.org/?SecuringNFS](http://wiki.debian.org/?SecuringNFS)
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=

# more nfs-kernel-server
# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or [http://wiki.debian.org/?SecuringNFS](http://wiki.debian.org/?SecuringNFS)
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

---

### Post by blueridgedog on 2009-06-24
It may be that some part of the networking system is not up when the mount occurs.  Just a guess and not a good one.  Are there any errors in the log?  

You could just put mount -a in /ect/init.d/rc.local.

---

### Post by ajmcello on 2009-06-25
No errors. I examined syslog, msesages, dmesg and stared at the screen at bootup. Everything seems fine. This appears to be a very common problem, existing in prior version of Ubuntu. Added mount -a to rc.local will work for now.

---

