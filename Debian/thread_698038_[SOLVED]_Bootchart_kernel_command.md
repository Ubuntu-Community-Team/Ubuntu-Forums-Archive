---
title: "[SOLVED] Bootchart kernel command"
date: 2008-02-15
forum: Debian
---

### Post by p_quarles on 2008-02-15
In Ubuntu, bootchart always configured itself to run on startup upon initial installation. In Lenny, apparently, I need to set it up myself. The man page for bootchartd says:
> bootchartd is commonly used to profile the boot process for the purpose of speeding it up.In this case, it is started by the kernel as the init  process.   This  is configured  by adding the init=/sbin/bootchartd option to the kernel command line -- either interactively or by editing the bootloader&#8217;s configuration file. Please refer to the  documentation  of your bootloader for details (e.g. lilo, grub or yaboot)Okay, I get this, I think: I need to add the command mentioned to the kernel line in /boot/grub/menu.lst. If I understand correctly, it would look like this:
```
kernel        /boot/vmlinuz-2.6.22-3-amd64 root=/dev/sda1 ro quiet init=/sbin/bootchartd
```Now, I'm asking for confirmation just because I'm still kind of wary of messing with grub. I imagine this would be perfectly simple to revert by booting into single-user mode if something goes wrong. Still, if I'm way off the mark in my thinking here, I'd appreciate any pointers. :)

---

### Post by kellemes on 2008-02-16
> **p_quarles said:**
> In Ubuntu, bootchart always configured itself to run on startup upon initial installation. In Lenny, apparently, I need to set it up myself. The man page for bootchartd says:
Okay, I get this, I think: I need to add the command mentioned to the kernel line in /boot/grub/menu.lst. If I understand correctly, it would look like this:
```
kernel        /boot/vmlinuz-2.6.22-3-amd64 root=/dev/sda1 ro quiet init=/sbin/bootchartd
```Now, I'm asking for confirmation just because I'm still kind of wary of messing with grub. I imagine this would be perfectly simple to revert by booting into single-user mode if something goes wrong. Still, if I'm way off the mark in my thinking here, I'd appreciate any pointers. :)

Simply copy/paste the kernel line.. and mess around with the copy.

```
title		Kernel I've beenmessing around with
root		(hd2,0)
kernel		/vmlinuz-2.6.22-3-686 root=/dev/sdb7 ro quiet 
initrd		/initrd.img-2.6.22-3-686
savedefault
```

As long as you leave the original alone, you'll be fine..

---

### Post by kellemes on 2008-02-16
Not sure if I understood your question by the way..
I assume you're worried the kernelline is wrong?

You can also edit the kernelline 'on the fly' by pressing 'e' when you highlighted a kernelline in your bootmenu.
See [http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu")

Can't help you with bootchart I'm afraid..

---

### Post by p_quarles on 2008-02-16
Yeah, I knew about editing it on the fly, but I wanted to try to figure out the correct edit to the menu.lst file. I'll try the extra entry idea. Thanks for the suggestion.

---

### Post by p_quarles on 2008-02-16
The menu.lst configuration I posted in my first post is correct. Adding that  command to the line causes bootchart to collect its data, and the image cannot be generated after bootup by running:
```
bootchart
```

EDIT: Oh and, for those interested, the boot time was 22 seconds, my best ever.

---

