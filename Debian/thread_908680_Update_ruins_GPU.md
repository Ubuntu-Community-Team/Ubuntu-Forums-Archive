---
title: "Update ruins GPU"
date: 2008-09-02
forum: Debian
---

### Post by dbbolton on 2008-09-02
A few weeks ago, I ran aptitude safe-upgrade and when I rebooted, I discovered that my GPU performance had tanked. I went from 4000 fps to 200 fps in glxgears. So, I installed the fglrx package along with the fglrx modules for 2.6.25-2-486. Afterward, everything was fine.

I upgraded again today, and the same thing happened. I rebooted and selected the 2.6.25-2-486 kernel. After booting, I made sure that fglrx and the modules packages were still installed, and they are. However, I'm only getting about 800 fps. I can't play games or run Compiz.

What should I do?

---

### Post by dbbolton on 2008-09-03
Solution: [http://forums.debian.net/viewtopic.php?t=17776](http://forums.debian.net/viewtopic.php?t=17776)

---

### Post by p_quarles on 2008-09-04
Isn't the 486 kernel kind of non-standard for a recent machine? My understanding was that the 686 arch was the appropriate 32-bit kernel for any x86 CPU since the Pentium II. 

If I'm wrong, I'd be interested in knowing more. :)

---

### Post by dbbolton on 2008-09-04
> **p_quarles said:**
> Isn't the 486 kernel kind of non-standard for a recent machine? My understanding was that the 686 arch was the appropriate 32-bit kernel for any x86 CPU since the Pentium II. 

If I'm wrong, I'd be interested in knowing more. :)
That is true, but I only found that out yesterday. Apparently the 486 was just installed by default because it is the "least common denominator" architecture. I have an Athlon XP. There used to be a K7 kernel, but they stopped developing it. However, I noticed that there is still a transitional package for K7 which simply installs the 686.

---

### Post by markharding557 on 2008-09-05
> **dbbolton said:**
> That is true, but I only found that out yesterday. Apparently the 486 was just installed by default because it is the "least common denominator" architecture. I have an Athlon XP. There used to be a K7 kernel, but they stopped developing it. However, I noticed that there is still a transitional package for K7 which simply installs the 686.

686 is the closest to k7.
check that upgrading has not reverted you to the open source driver which indeed is poor at 3d.
If you haven't already install fglrx-control,then look in its info tab.
If it says mesa then you are using open source drivers and need to reinstall fglrx

---

### Post by dbbolton on 2008-09-05
> **markharding557 said:**
> 686 is the closest to k7.
check that upgrading has not reverted you to the open source driver which indeed is poor at 3d.
If you haven't already install fglrx-control,then look in its info tab.
If it says mesa then you are using open source drivers and need to reinstall fglrx
I had to recompile the kernel headers, and that seemed to do the trick.

---

