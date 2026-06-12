---
title: "/proc/sys/sunrpc/nfsd_debug - permission denied"
date: 2009-01-10
forum: General Help
---

### Post by sukadevb on 2009-01-10
I am trying to debug an NFS problem with my ubuntu 8.04
system as the server. But I get this:

    $ sudo echo 32767 > /proc/sys/sunrpc/nfsd_debug
    bash: /proc/sys/sunrpc/nfsd_debug: Permission denied

    $ cat /proc/sys/sunrpc/nfsd_debug
    0

I quickly checked a Fedora 9 system and above write
command also works. Is there a different way to enable
debug on Ubuntu ?

Thanks

---

### Post by taurus on 2009-01-10
Try adding a second sudo in there.

```
sudo echo 32767 > sudo /proc/sys/sunrpc/nfsd_debug
```

---

