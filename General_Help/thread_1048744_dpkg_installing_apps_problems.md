---
title: "dpkg installing apps problems"
date: 2009-01-23
forum: General Help
---

### Post by And6ate9 on 2009-01-23
I tried installing some apps today but it seems that something is wrong with the dpkg system it told me that

"dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

so I did then it told me that

"Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic.bak
Cannot find /lib/modules/2.6.24-23-generic.bak
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic.bak
dpkg: subprocess post-installation script returned error exit status 1"

and it did not fix my problems. Did Ubuntu lie to me? Does it not love me? Why Ubuntu why?

---

### Post by taurus on 2009-01-23
Try

```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

