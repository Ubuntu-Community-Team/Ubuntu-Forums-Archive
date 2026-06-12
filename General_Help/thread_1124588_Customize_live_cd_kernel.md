---
title: "Customize live cd kernel"
date: 2009-04-13
forum: General Help
---

### Post by dschaefer79 on 2009-04-13
Hi,

I've read the livecd documentation customization [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) 
 and it doesn't work for what I will do. I have Ubuntu 9.04 installed on my machine.

What I will do is to boot the desktop cd Ubuntu 9.04 to a custom kernel 2.6.29.1 by default
So what I've done, I downloaded a desktop cd Ubuntu 9.04 beta and  followed your instruction and when it comes to kernel
customisation, I've done this.

1. I've installed a 2.6.29.1 kernel on my computer.
2. I've copied vmlinuz-2.6.29.1 kernel from my installation to extract-cd/casper/vmlinuz and to edit/boot too.
3. I've copied initrd-2.6.29.1 from my installation to extract-cd/casper/initrd.gz in gzip compressed file and to edit/boot too.
4. I've symlinked vmlinuz-2.6.29.1 kernel from /edit/boot to /edit/vmlinuz
5. I've symlinked initrd-2.6.29.1 from /edit/boot to /edit/initrd.img

and after I create the iso file from your instruction and it boots. But now I get a kernel panic - not syncing: VFS: Unable to mount root fs
on unknown-block(8,50).

Do you know any option to build with the kernel so I don't get this kernel panic ? Or it is something else ?

I want also to change the kernel package the desktop cd installs on the harddisc, But I don't know how, I didn't found any documentation
on how to do this I have already the package made myself.

Thanks for help,

---

