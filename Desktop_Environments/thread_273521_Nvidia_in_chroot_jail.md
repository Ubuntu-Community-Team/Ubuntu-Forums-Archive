---
title: "Nvidia in chroot jail?"
date: 2006-10-08
forum: Desktop Environments
---

### Post by Xilon on 2006-10-08
Note: I have no experience in chroots, I havn't set one up yet, I just want to know if this can be done and if it would work.

I have just installed Debian Etch and I would like to install the nvidia-glx 1.0.9625 drivers, but this is a beta driver and I don't want it to screw up teh system. I will most likely be setting up a chroot jail for some applications which I want to be bleeding edge, and  I would also like to put nvidia into this jail. The thing I'm not sure about is would the nvidia drivers actually work inside a jail? And would I be able to install compiz/beryl into this jail (or seperately) and have it work?

The thing that doesn't allow me to simply use the experimental non-free repo from debian is that it wants to update heaps of other packages which I don't want. Is there possibly a way of getting just nvidia from the repo (and having it update automatically - just downloading and installing the .deb doesn't cut it) ?

Could someone also point me in the right direction to setup a chroot? :)

Sorry if I posted in the wrong section since it's about Debian...

---

### Post by TheeMahn2003 on 2006-12-21
> **Xilon said:**
> Note: I have no experience in chroots, I havn't set one up yet, I just want to know if this can be done and if it would work.

I have just installed Debian Etch and I would like to install the nvidia-glx 1.0.9625 drivers, but this is a beta driver and I don't want it to screw up teh system. I will most likely be setting up a chroot jail for some applications which I want to be bleeding edge, and  I would also like to put nvidia into this jail. The thing I'm not sure about is would the nvidia drivers actually work inside a jail? And would I be able to install compiz/beryl into this jail (or seperately) and have it work?

The thing that doesn't allow me to simply use the experimental non-free repo from debian is that it wants to update heaps of other packages which I don't want. Is there possibly a way of getting just nvidia from the repo (and having it update automatically - just downloading and installing the .deb doesn't cut it) ?

Could someone also point me in the right direction to setup a chroot? :)

Sorry if I posted in the wrong section since it's about Debian...

For a live dvd / cd I certainly have not had 100% success with NVidia I have gotten beryl working with intel & beryl on the live dvd can install beryl & nvidia drivers.  I have also written a rmod for installing nvidia divers in a chroot envior.  I write software for the [reconstructor team]("http://reconstructor.aperantis.com/").  I also highly suggest you read my post on the [subject]("http://ubuntuforums.org/showthread.php?t=309704") & my [Howto]("http://ubuntuforums.org/showthread.php?t=310212").  Grab my nvidia rmod from reconstructors website and view the source.

---

