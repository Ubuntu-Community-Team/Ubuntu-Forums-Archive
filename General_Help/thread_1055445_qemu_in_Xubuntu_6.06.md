---
title: "qemu in Xubuntu 6.06"
date: 2009-01-30
forum: General Help
---

### Post by doglover56 on 2009-01-30
Hello and thanks in advance for your help.

I am running Xubuntu 6.06 because any newer version won't run on my machine because of hard disc incompatibilities with newer versions. It came with qemu 0.8. The newest version in backports is 0.82. The newest version elsewhere is 0.91. Since the newest backport is 0.82, do I interpret that as saying that 0.91 will not work on X 6.06? Or does it mean nobody has tried it, and I have to build it myself and risk trashing my system. Of course it doesn't help that I have never built software, but that is another issue..

IMF

---

### Post by txcrackers on 2009-01-31
You'll need to build it yourself. It's not that hard and, no, it won't "trash your system."

---

### Post by doglover56 on 2009-02-01
OK, I am trying this building idea, but really have no idea. I am using Xubuntu 6.06, and want QEMU 0.91 which is not available as a package for this distribution, so I have to build it.
QEMU documentation says you have to have gcc 3, not 4. Apparently it is not installed. So I use synaptic to install the packages gcc-3.4, gcc-3.4-base, and gcc-3.4-doc. So then I go into the QEMU folder, type ./configure, but it says:
ERROR: "gcc" either does not exist or does not work
I type "whereis gcc" and I get "gcc: /usr/lib/gcc", and all there is in there is some header files and the like.
I type "whereis gcc-3.4", and get "gcc-3: /usr/bin/gcc-3.4 /usr/bin/X11/gcc-3.4". When I type gcc-3.4 -v, it tells me it is version 3.4.6, so it is there.
What am I doing wrong?
Thanks,
IMF

---

### Post by cnheying on 2009-02-24
> **doglover56 said:**
> OK, I am trying this building idea, but really have no idea. I am using Xubuntu 6.06, and want QEMU 0.91 which is not available as a package for this distribution, so I have to build it.
QEMU documentation says you have to have gcc 3, not 4. Apparently it is not installed. So I use synaptic to install the packages gcc-3.4, gcc-3.4-base, and gcc-3.4-doc. So then I go into the QEMU folder, type ./configure, but it says:
ERROR: "gcc" either does not exist or does not work
I type "whereis gcc" and I get "gcc: /usr/lib/gcc", and all there is in there is some header files and the like.
I type "whereis gcc-3.4", and get "gcc-3: /usr/bin/gcc-3.4 /usr/bin/X11/gcc-3.4". When I type gcc-3.4 -v, it tells me it is version 3.4.6, so it is there.
What am I doing wrong?
Thanks,
IMF

can you try something like this?

./configure CC=/usr/bin/gcc-3.4

---

