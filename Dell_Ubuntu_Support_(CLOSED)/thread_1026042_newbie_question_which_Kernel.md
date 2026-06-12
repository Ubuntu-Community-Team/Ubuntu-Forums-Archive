---
title: "newbie question which Kernel"
date: 2008-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nfyllas on 2008-12-30
Hello all
Just setup 8.04 two days ago on an Dell 1525, came with Vista
I used the DVD image from Dell-linux site
No big issues; wi-fi fixed after updating
a newbie question though

My kenrel:
2.6.24-22-generic

is this the right one to use for fully utilising the 
core 2 processor?

Thanks

---

### Post by llamakc on 2008-12-30
Yes. The older versions of Debian (and Debian-based distros) had kernel images that were specified with -smp or architecture type (k7 for AMD). The current *-generic kernel takes advantage of your dual cores. You can check to see if they are picked up by opening a Terminal and typing:

```

cat /proc/cpuinfo

```

or by adding the CPU Frequency Scaling applet to your gnome-panel.

---

### Post by nfyllas on 2008-12-30
Ok thanks, dual cores are on

---

