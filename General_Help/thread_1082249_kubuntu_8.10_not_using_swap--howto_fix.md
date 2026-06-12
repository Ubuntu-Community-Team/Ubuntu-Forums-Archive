---
title: "kubuntu 8.10 not using swap--howto fix?"
date: 2009-02-27
forum: General Help
---

### Post by MikeB23930 on 2009-02-27
I can manually turn swap on but after I reboot kubuntu 8.10 no longer recognizes/uses swap space.  How can I make kubuntu automatically use swap space on boot?

Thanks,

Mike

---

### Post by internalkernel on 2009-02-27
Did you check your /etc/fstab? To make sure your swap is defined properly, check to make sure the UUID is correct by: 

```
sudo vol_id /dev/sdX
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=d7791f85-6ac2-44c3-a107-0e8d15b6242d
ID_FS_UUID_ENC=d7791f85-6ac2-44c3-a107-0e8d15b6242d
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

Your looking for ID_FS_UUID_ENC= 

You could always try destroying the swap partition and re-creating it... Make sure to adjust the above entry in fstab though.

---

### Post by MikeB23930 on 2009-02-27
Internalkernel,

The uuid for the swap partition in fstab was wrong.  Swap seems to be working correctly now.

Thanks,

Mike

---

