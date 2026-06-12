---
title: "fstab not mounted at boot"
date: 2009-06-16
forum: General Help
---

### Post by carloshiga on 2009-06-16
Hi all,

I'm trying to set up a nfs server/client using Ubuntu. I put the following in the /etc/fstab file in the client:

```
192.168.0.3:/data /mount_point nfs rw,exec,auto,users 0 0
```

(where users is a group name) and then

```
sudo mount -a
```

After this, everthing is working fine. But if I restart the client machine the nfs file system is not mounted automatically, so I need to use the mount command again. I thought that the 'auto' option would solve this but it did not. Is this problem related to the firewall?

---

### Post by Cheesemill on 2009-06-16
How are you connected to your network?

It could well be that fstab is trying to mount your NFS share before your network is up (this is especially a problem with wireless as the network doesn't come up until after you've logged on).

---

### Post by carloshiga on 2009-06-16
The nfs-client and nfs-server are connected by a local network.

nfs-client: 192.168.0.200
nfs-server: 192.168.0.3

The nfs-client has access to the internet via a second network card and the IP address is obtained via DHCP. The nfs-client is also configured as a router and I use a simple switch to connect the other machines, including the nfs-server, to the internet.
I don't know if the network service is initialized before the fstab is mounted.

---

