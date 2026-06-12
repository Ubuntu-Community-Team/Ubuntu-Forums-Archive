---
title: "Using a newly downloaded Kernel i686"
date: 2005-02-11
forum: Desktop Environments
---

### Post by gherikill on 2005-02-11
I downloaded the i686 kernel using synaptic but it appears that my system is still using the i386 kernel to boot.  How do I change it so that Ubuntu uses the 686 optimized kernel.

I'm using Warty.

Thanks

---

### Post by alastair on 2005-02-11
I have never actually done this on Ubuntu/Debian (still testing) - but this is something that you would want to choose from the GRUB boot screen i.e.

Press "ESC" key at boot to get a GRUB menu - this lets you select kernels to boot.

The GRUB config file is :  /boot/grub/menu.lst

Be very careful with this stuff.

---

### Post by brousch on 2005-02-11
When you reboot your computer, there should be a list of kernels to choose from soon after the BIOS shows its stuff.

You may have to press ESC, like alastair said, but it always comes up for me (there is an option in /boot/grub/menu.lst to change that behavior).

I dual boot Ubuntu and WinXP, and this list always shows up for 5 seconds, then selects the default Ubuntu kernel automatically.

You should press the down arrow during these 5 seconds to get a better look at the list. If the i686 kernel is not the default, you can edit the list right there.

Be careful what you change, as you can make your computer unbootable by messing things up too much.

---

