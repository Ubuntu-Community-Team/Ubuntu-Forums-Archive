---
title: "NFS, Can't figure out what I'm doing wrong"
date: 2011-07-03
forum: Desktop Environments
---

### Post by BloodyIron on 2011-07-03
Hi Folks,

So I'm trying to setup a PXE boot server, and in the process of that I am trying to setup a NFS share to mount part of what I'm trying to boot to.

So as a test I am trying to mount a share I have setup logged into the local system.

my /etc/exports has this:

```
/var/lib/tftpboot 10.0.0.*(rw,no_root_squash,async,insecure)
```

I'm trying the following command (and variant):

```
mount 10.0.0.48:/var/lib/tftboot test

mount -t nfs4 -o proto=tcp,port=2049 10.0.0.48:/var/lib/tftboot test
```

When I try to mount the share, logged in as root (STRICTLY FOR TESTING) I get the following error:

```
mount.nfs4: access denied by server while mounting 10.0.0.48:/var/lib/tftboot
```


Now, I've read multiple howto's on PXE booting, and dealing with NFS shares, and I can't for the life of me figure out what I'm doing wrong. I'm using a default installation of Ubuntu 10.04 in a VM, desktop edition.

I have run out of ideas, and I would greatly appreciate what help I can get.

---

### Post by Chrysostomos on 2011-07-04
But your /etc/exports looks like an old style nfs v3 export.

---

### Post by Lars Noodén on 2011-07-04
You might look at [dnsmasq](http://packages.ubuntu.com/natty/dnsmasq).  I find that it is very, very easy to set up TFTP service with it and have used it extensively for PXE booting.  Again, it's very easy to set up.

---

