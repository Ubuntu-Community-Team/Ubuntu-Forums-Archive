---
title: "n00b question about kernel modules"
date: 2007-06-01
forum: Desktop Environments
---

### Post by penguins! on 2007-06-01
I've been having terrible problems with the proprietary ATI drivers and recently discovered that it was because the wrong version of the fglrx kernel module was being loaded.

I solved the problem by doing the following

```

rmmod fglrx
sudo insmod /lib/modules/2.6.20-16-generic/misc/fglrx.ko
modprobe fglrx

```

I then restart X and the drivers work fine.

Now I don't really understand how the whole process of loading modules works yet.

My problem is that this has to be done every time I reboot. Is there any way to make sure the fglrx module loads at boot time?

This is what my /etc/modules file looks like:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
kvm-intel
fglrx

```

Adding fglrx there did nothing.

Any help would be appreciated. Thanks!

---

