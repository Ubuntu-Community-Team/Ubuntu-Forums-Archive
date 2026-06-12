---
title: "Add/Remove Programs error"
date: 2009-02-04
forum: General Help
---

### Post by 0x68 on 2009-02-04
The following is reported any time I install a package through Add/Remove Programs:

```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kerne/postinst.d/dkms
run-parts: executing /etc/kerne/postinst.d/nvidia-common
run-parts: /etc/kerne/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.postinst line 1181.
dpkg: error processing linux-image-2.6.28 (--configure):
 subprocess post-installation script returned error exit status 2

```

This began after I compiled a new kernel without any support for nvidia cards. Fortunately, it appears that the packages are actually installing fine.

Thanks!

---

