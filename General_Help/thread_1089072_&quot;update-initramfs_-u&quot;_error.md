---
title: "&quot;update-initramfs -u&quot; error"
date: 2009-03-06
forum: General Help
---

### Post by quini on 2009-03-06
Hi,

I installed a selfcompiled kernel, built using the make-kpkg command (it creates a deb package); I later uninstalled it.

Now, every time the command "update-initramfs -u" is run, I get an error referred to that kernel:

```
root@quinitz:~/tmp# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.28.6-628l
Cannot find /lib/modules/2.6.28.6-628l
update-initramfs: failed for /boot/initrd.img-2.6.28.6-628l
```

The linux-image-2.6.28.6-628l package is already uninstalled:

```
root@quinitz:~/tmp# aptitude search 2.6.28.6-628l
c   linux-image-2.6.28.6-628l       - Linux kernel binary image for version 2.6
```

I have already checked the /etc/initramfs-tools directory and found nothing related to that kernel:

```
root@quinitz:/etc/initramfs-tools# grep -r linux-image-2.6.28.6-628l *
root@quinitz:/etc/initramfs-tools#
```


Any idea?  Right now I must solve this problem by installing that package, then uninstalling it.

TIA  ;)

---

### Post by quini on 2009-03-06
Hi again!

I've found the problem... there's a text file in /var/lib/initramfs-tools, called 2.6.26.6-628l...

That probably should have been deleted once the package was removed, but it did not.

Deleting it solves the problem  8-)

I'm sorry for your time  ;)

---

### Post by balaji31d on 2011-01-24
> **quini said:**
> Hi again!

I've found the problem... there's a text file in /var/lib/initramfs-tools, called 2.6.26.6-628l...

That probably should have been deleted once the package was removed, but it did not.

Deleting it solves the problem  8-)

I'm sorry for your time  ;)


Thanks buddy! You saved me :)

---

### Post by quini on 2011-01-24
> **balaji31d said:**
> Thanks buddy! You saved me :)

You're welcome  ;)

---

