---
title: "VGA Console Query"
date: 2006-01-11
forum: General Help
---

### Post by nelposto on 2006-01-11
Hey,

A while back I was having a problem with newly compiled kernels giving a blank screen after being chosen in GRUB until they had booted. I found eventually that this was a problem with the line "vga=xxx" in my menu.lst. Putting this at "vga=normal" fixes the problem, but leads to an ugly low resolution console.

The reason newly compiled kernels wont accept this command is because of some option not being enabled in the config when compiling the kernel. Someone posted this a few months back and I've been combing the forums recently since I reinstalled ubuntu the other day, but I haven't managed to find it.

I can't remove the "vga=xxx" line from my bootloader as this laptop I'm using wont display properly otherwise.

So if anyone knows the correct options I must enable/disable in my kernel config before compiling, I would apppreciate it very much.

Thanks

---

### Post by mcduck on 2006-01-11
what is your displays native resolution? For 1024*768 with 16M colors the line is 'vga=792'. [Here]("http://www.damnsmalllinux.org/wiki/index.php/Vga%3Dxxx") is a nice table with some of most common display modes for Grub.

---

### Post by nelposto on 2006-01-11
Edited : PMG I found it..

[http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69](http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69)

---

