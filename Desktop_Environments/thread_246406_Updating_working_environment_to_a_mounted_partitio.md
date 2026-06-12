---
title: "Updating working environment to a mounted partition"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Mikeee on 2006-08-29
Hello all,

Using the Ubuntu LiveCD is it possible to mount a partition with an installed ubuntu on and then navigate to this directory and somehow update the working environment so you are actully using this mounted partition instead of the livecd? For those of you familiar with gentoo im asking for the same as the env-update script.

Thanks

---

### Post by gerbman on 2006-08-29
What do you mean by "working environment"? You can definitely mount Ubuntu partitions from the LiveCD. Just do something like this:```
sudo mkdir ubuntu_home
sudo mount -t ext3 /dev/hda1 ~/ubuntu_home
```That will mount the Ubuntu partition /dev/hda1 (your device might be different) at ~/ubuntu_home.

---

### Post by bensexson on 2006-08-29
Look into chroot.

---

