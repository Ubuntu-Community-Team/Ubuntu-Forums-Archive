---
title: "nfs mount fails"
date: 2011-02-18
forum: Desktop Environments
---

### Post by R. M. Frank on 2011-02-18
Hi, 
I'm banging my head on this.
I have Ubuntu 10.10 x86_64 installed and running on a MacMini (latest generation). I have installed nfs-common and portmap - no errors. No firewall active (to my knowledge!)

I have configured the server (fedora 7) to export file systems via nfs (version 3), other machines on the same network (fedora 10) can import with no problems.

But: whenever I do 'sudo showmount -e <host>' on the ubuntu client, I get:
clnt_create: RPC: Program not registered

statd and portmap are up and running.
For 'sudo mount -v -t nfs <host>:/mirror/network /Network' (/Network exists) I get:

mount.nfs: timeout set for Fri Feb 18 22:00:58 2011
mount.nfs: trying text-based options 'vers=4,addr=###.###.83.1,clientaddr=###.###.83.26'
mount.nfs: mount(2): No such file or directory
mount.nfs: trying text-based options 'addr=###.###.83.1'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query retrying: RPC: Program not registered

mount.nfs: prog 100003, trying vers=3, prot=17
mount.nfs: portmap query failed: RPC: Program not registered

mount.nfs: prog 100003, trying vers=2, prot=6
mount.nfs: portmap query retrying: RPC: Program not registered

mount.nfs: prog 100003, trying vers=2, prot=17
mount.nfs: portmap query failed: RPC: Program not registered

mount.nfs: prog 100003, trying vers=2, prot=6
mount.nfs: portmap query retrying: RPC: Program not registered

mount.nfs: prog 100003, trying vers=2, prot=17
mount.nfs: portmap query failed: RPC: Program not registered

mount.nfs: requested NFS version or transport protocol is not supported

and no entries in the logs of either the client nor the server.
I've checked several forums, websites, google, etc. But none have any suggestions beyond what I have. (Installed nfs-common, portmap, start the daemons, make sure no firewall, mount point exists, server IS exporting, etc). Several forums tell the user to start nfs-common. I have no such service on 10.10 - is there something missing?

I currently have two such systems, both behaving identically.

Thanks for any help
-Robert

---

### Post by dabl on 2011-02-18
Here's a very good guide to NFS networking:  [http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

Hope it helps.

---

### Post by twyufe on 2011-03-07
For me it's the same. I even did install my NAS again, but the problem stays.

Message: mount.nfs: access denied by server while mounting 192.168.123.1:/mnt/nfs-data/

Exactly the same mount command to this NAS works, with 10.04 LTS and Opensuse 11.3

---

### Post by deconstrained on 2011-03-07
> **twyufe said:**
> For me it's the same. I even did install my NAS again, but the problem stays.

Message: mount.nfs: access denied by server while mounting 192.168.123.1:/mnt/nfs-data/

Exactly the same mount command to this NAS works, with 10.04 LTS and Opensuse 11.3

It's almost always a configuration issue when these sorts of things happen. Double-check everything on both client/server side and restart the NFS kernel/server/client.

---

### Post by OpenMinded on 2011-05-16
> **deconstrained said:**
> It's almost always a configuration issue when these sorts of things happen. Double-check everything on both client/server side and restart the NFS kernel/server/client.

well sorry, but that does not help at all.
requested NFS version or transport protocol is not supported

Any one has a fix?
I have the same issue as reported before.

Might there be an IP block?

---

### Post by brendanpiater on 2012-01-24
In case this can help others.

I had this error after changing the IP address range of my internal network. 

I forgot to update the portmap rules to allow the new IP address range to connect to the NFS server.

After updating portmap, restarting portmap and re-exporting shares I was able to mount the NFS shares again.

---

