---
title: "installing ubuntu over the network..."
date: 2008-12-28
forum: General Help
---

### Post by Mia_tech on 2008-12-28
guys, I have downloaded the Alternate iso and extracted its content and put it on the server, I'm able to boot the client via pxe, but I would like for someone to help me how could I boot the client and start pulling the install from the server, I'm suspecting that I would have to modify the "default" file that is part of the network installation... 

any help appreciated

---

### Post by taurus on 2008-12-28
Maybe one of these methods works for you.

[https://help.ubuntu.com/community/Installation#Server and network installations](https://help.ubuntu.com/community/Installation#Server and network installations)

---

### Post by Mia_tech on 2008-12-28
I'm trying to do the live cd approach in the link avobe... but the content of the iso image is not on an ubuntu server, is on a windows 2003 server, so I don't know how to modify the pxelinux.cfg/default file for this particular scenario, here's the content of the default file

```
LABEL live
kernel ubuntu-desktop/casper/vmlinuz
append initrd=ubuntu-desktop/casper/initrd.gz boot=casper netboot=nfs nfsroot=192.168.0.10:/mnt/u01/tftpboot/ubuntu-desktop -- 

```

I tried changing the ip address, but that wasn't enough as windows speaks smb, and the protocol use by the default file above is nfs... how could I make this work for my particular scenario... is it possible to access the share using smb instead?

thanks in advance

---

### Post by Mia_tech on 2008-12-28
finally got it working as soon as I hosted the alternate cd on the ubuntu server with apache everything worked just fine, what makes me think the reason why it didn't work before was b/c a misconfig on IIS in windows 2003...

---

