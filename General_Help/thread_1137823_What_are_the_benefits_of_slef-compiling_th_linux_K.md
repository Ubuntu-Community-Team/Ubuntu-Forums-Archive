---
title: "What are the benefits of slef-compiling th linux Kernel?"
date: 2009-04-25
forum: General Help
---

### Post by inxygnuu on 2009-04-25
I have been looking around at compiling the Linux Kernel lately, and i was wondering what advantages self-compiling the Linux kernel has?

Thanks,
3v4n:)

---

### Post by Peasantoid on 2009-04-25
Customization.

Other than that, I don't recommend it unless you really know what you're doing.

---

### Post by lisati on 2009-04-25
I'm with Peasantoid on this one: about the best I could come up with is if your system is a bit weird and needed some kind of special tinkering. Not for the faint-hearted or inexperienced.

---

### Post by mb_webguy on 2009-04-25
The only reason I can think of that a normal desktop user might possibly consider recompiling the kernel is if he was using a 32-bit architecture and wanted to use more than 4GB of physical memory.  You could recompile the kernel with PAE enabled to allow for up to 64GB of physical memory on a 32-bit system.

---

### Post by inxygnuu on 2009-04-25
okay. i read that it would potentially make the system faster, and that you can install drivers by compiling it.

---

### Post by Peasantoid on 2009-04-26
Most drivers come as LKMs (Loadable Kernel Modules), so you don't need to compile them into the kernel.

---

### Post by Wiebelhaus on 2009-04-26
It's easy and fun and your in complete control.

[Here's a how to]("https://help.ubuntu.com/community/Installation/LowMemorySystems") , more or less , it's not ***_true_*** compiling but whatever this will either intrigue you more or totally make you sick.

---

### Post by inxygnuu on 2009-04-27
> **sx66gns said:**
> It's easy and fun and your in complete control.

[Here's a how to]("https://help.ubuntu.com/community/Installation/LowMemorySystems") , more or less , it's not ***_true_*** compiling but whatever this will either intrigue you more or totally make you sick.

To me that is just building your own system out of a Ubuntu minimal install. Very cool though.:)

---

### Post by mb_webguy on 2009-04-27
If you're still considering compiling your own kernel, you should read [this]("http://ubuntuforums.org/showthread.php?t=311158").

---

