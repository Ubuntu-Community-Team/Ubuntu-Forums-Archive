---
title: "How to install Gentoo together with Ubuntu"
date: 2006-05-10
forum: Desktop Environments
---

### Post by MichaelZ on 2006-05-10
Hello,

I would like to give a try to Gentoo. Therefore I would like to install it along with my Ubuntu. I use LVM with Ubuntu and I am not sure if this woul be a problem when installing Gentoo (from Live CD, stage 3), e.g, during the partitioning step.

Thank you very much.

Best wishes,
Michael

---

### Post by hw-tph on 2006-05-10
Since you already have a running system you don't really need a livecd. Just partition and extract the stage tarball from within Ubuntu and then chroot over to your new Gentoo root partition.

However, if you have your entire disk used by lvm you will probably need to boot from a livecd and resize it or set up your lv's.

I suggest you, if possible, install a secondary disk and install Gentoo on it to avoid messing with your existing lvm setup. Then use the already installed Grub as supplied by Ubuntu to boot Gentoo.


Håkan

---

### Post by MichaelZ on 2006-05-10
Hello,

Thank you for your help. The desktop where I want to install Gentoo is not mine, but belong to my Institute. It is an old computer that I could use for learn Linux and particurarly Ubuntu. My intention is to make some free space and give Gentoo a try. If I mess my sysem, I will simply re-install it. It would not be so tragic.

I have found this link, which could be an alternative to the Live CD:

[http://www.wikihow.com/Install-Gentoo-Linux-from-Ubuntu-Breezy-Badger]("http://www.wikihow.com/Install-Gentoo-Linux-from-Ubuntu-Breezy-Badger")

Best wishes,
Michael

---

