---
title: "update breaks system theme"
date: 2006-07-12
forum: Desktop Environments
---

### Post by peterthewolf on 2006-07-12
Not just nvidia but my dwl-g122 wireless adaptor stopped working.
linux 2.6.15-25 works
linux 2.6.15-26 activity light never flashes so no works

---

### Post by tseliot on 2006-07-12
> **peterthewolf said:**
> Not just nvidia but my dwl-g122 wireless adaptor stopped working.
linux 2.6.15-25 works
linux 2.6.15-26 activity light never flashes so no works

Try this:

Boot in kernel 2.6.15-25
type:
```
uname -r
```

you will get something like "2.6.15-26-[COLOR="Red"]k7[/COLOR]"

The part in red ("k7" in this case) stands for the architecture your kernel is optimised for (it can also be "686", "386", etc.)

Type:
sudo apt-get install linux-k7 (or linux-386, etc. according to your architecture)

then reboot (boot in the new kernel) and you will have the kernel modules for your new kernel

---

### Post by peterthewolf on 2006-07-13
uname-r gives 2.6.15-25-38
sudo apt-get install linux-386 says already installed and takes no action
so no effect on problem

---

### Post by philippe_carlo on 2006-07-13
Getting the NVIDIA driver back to work is easy. Uninstall them, next reinstall them. They need to be compiled agains your kernel to work, which happens during installation.

The same probably holds for your wireless card. Did you compile the modules yourself? In that case, you need to recompile and reinstall them while you are running the new kernel.

---

### Post by peterthewolf on 2006-07-13
Sorry to confuse the nvidia reference is to another users problem I do not have a nvidia card

[http://www.ubuntuforums.org/showthread.php?t=214261&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=214261&highlight=nvidia)

was just another comment about release too soon

---

