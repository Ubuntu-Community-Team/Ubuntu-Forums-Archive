---
title: "GRUB boot loader USB"
date: 2011-01-26
forum: Desktop Environments
---

### Post by Alxl on 2011-01-26
I have installed Ubuntu 10.10 Minimal on a 2GB USB using CLI and it is working very well after adding a  few applications. But  this USB will be used only on machines other than my own - likely with Windows as the only OS.  And it is not comfortable for me to go into the BIOS of a strange machine to change the order of booting and afterwards go back to reset the order , especially with the owner looking on,  obviously worried, and wandering whether his machine will still be working!


    
    So my question: Is there any way to boot from a USB without having to go into the BIOS?
    I refer to this : 
    ```
GRUB can boot just about any other boot loader by chainloading.  The other boot loader then takes over and does the booting.  
We can boot other Gnu - Linux loaders like LiLo or GRUB Legacy, GAG Boot Manager, and we can even boot foreign proprietary
 boot loaders too. In fact, chainloading is the only way to boot a Microsoft Windows system from GNU GRUB.
```

 I am not familiar with the many intricacies of GRUB and don&#8217;t  know what &#8216;chainloading&#8217; is.


    
    Any advice will be appreciated. Essentially, I need to be able to boot machines using GRUB 2 on my USB.

---

### Post by oldfred on 2011-01-26
Chainload is just using one boot loader to boot another boot loader. Windows in the MBR just jumps to the active partition (boot flag) and that continues the boot. Grub chainloads to windows by just jumping to the windows partition and then windows takes over.

With MBR (msdos) partitioning and BIOS systems, you only boot the primary master drive. Newer systems with SATA let you choose which device is in effect the primary master. I do not know of any way to redirect BIOS from choosing which device to boot. Each system may also be set differently as some may have floppy first, or CD first and still boot HD as floppy or CD is empty.

You should be able on most newer system that also boot USB, just choose the one time boot key (f12 on mine) and boot your USB key. It will not change anything.

---

