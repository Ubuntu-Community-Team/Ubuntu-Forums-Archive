---
title: "compliling kernel ubuntu 8.04LTS"
date: 2008-12-13
forum: General Help
---

### Post by Merlin337W on 2008-12-13
New to the forum, if there is a place where this would be better suited feel free to direct me in that ... direction.

I'm attempting to compile my own kernel from the source packages online. Whenever I try and 'make menuconfig' I get an error saying I need [Ncurses] installed. Will be more specific if reply.

Relatively new to this type of OS environment, any help would be greatly appreciated.

-cheers.

---

### Post by tigerstripedcat on 2008-12-13
If you want to compile a vanilla kernel, do yourself a favor and use kernelcheck, it's so much easier than going through all those commands yourself.

TSC

---

### Post by albinootje on 2008-12-13
You mean [http://kcheck.sourceforge.net/about.html](http://kcheck.sourceforge.net/about.html) ?
I'd like to try it. Thanks for mentioning this.

---

### Post by sdennie on 2008-12-13
If you want to go about it manually, you should first install the following:

```

apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

```

This guide is old but, it's how I learned to compile kernels: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Sorivenul on 2008-12-14
The guide vor posted is excellent.  The [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") here on the forums is also informative and helpful.

---

