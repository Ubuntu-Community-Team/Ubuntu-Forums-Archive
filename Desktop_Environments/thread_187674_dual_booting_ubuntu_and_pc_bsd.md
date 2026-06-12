---
title: "dual booting ubuntu and pc bsd"
date: 2006-06-03
forum: Desktop Environments
---

### Post by zapcojake on 2006-06-03
Hello, I am running Dapper as my primary os and would like to try PCbsd.  I have installed Pcbsd but its boot loader crashes when I try to select linux to boot and Grub/ubuntu doesn't seem to recognize the bsd install/partition.  The ubuntu partitioner sees the bsd partition and the boot flag but says the filesystem is bad.  Is there any way to get it working? Thanks

---

### Post by turbojugend_gr on 2006-06-03
Since you never got it working, try to re-install, set the bootable Flag on for your BSD partition. If you get another bad filesystem flag you should propably check your patitioning tool for misbehaviour (most propably the built-in BSD partitioner). I assume that you have your Grub configured nicely to boot BSD, if you are not sure of this, try a manual booting to check this.

---

### Post by zapcojake on 2006-06-03
I had it working (bsd) just fine but the boot loader wouldn't load Ubuntu.  I rescued my Ubuntu installation with the cd and then Bsd wasn't shown in the Grub menu.  Did I miss a step or did something go wrong?

---

