---
title: "Apt-get problems wiht libc6"
date: 2006-06-18
forum: Desktop Environments
---

### Post by nousplacidus on 2006-06-18
Ok so heres the story:

I wanted to install the lastest deb of linuxdcpp and that requires a newer version of libc6 that ubuntu is not up to yet. So I tried to download their version of lib6 and install it and now its broken. 

any ideas?

I hope theres a simple solution to this.

---

### Post by 5-HT on 2006-06-18
Ouch, libc6 is a *very* important package: it is a dependency for many programs on your system.
There will be no easy way to use a non-Ubuntu libc6.

Can you simply reinstall Ubuntu's libc6?

If not, you may have to chroot into your system using a live CD and reinstall the proper libc6.
If you do not know how to chroot into your system, one way to do it is documented  under  'last resort 2' in  [https://wiki.ubuntu.com/LostPassword]("https://wiki.ubuntu.com/LostPassword")
(you'll need to modify the guide according to what your root partition happens to be. i.e., hda1, sda2, etc.).

Instead of changing your password in the chroot as the wiki describes, install libc6 with synaptic/apt/aptitude.

Hope that helps.

---

