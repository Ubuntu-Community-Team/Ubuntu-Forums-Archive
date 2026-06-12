---
title: "Chainload another disk?"
date: 2009-02-12
forum: General Help
---

### Post by bcgirten on 2009-02-12
Hello.

I'm not very new to the Linux world, or even to Ubuntu, however I do have a question that I'm having a hard time tracking a detailed answer for.

I've recently been working on a project for a multiboot USB live environment, and it's gone particularly well.  I've custom built a couple of different live distros onto the thumb drive, and currently have Grub loading them correctly, however what I'd like to do is add an entry in menu.lst that will boot to the hard drive of the machine.

I know what you're thinking.. just chainload Windows as listed in the example in the menu.lst file that comes with the default install.  There's a small caveat.

My system, and possibly several others that may end up using dd'ed copies of this flash drive, is a multiboot system running both WinXP and Intrepid, and possibly some others in the future.  Given that kernels are updated more often than I'd like to have to update this flash drive and consequently the image that is made from it, and that it will be used on systems under different configurations, is there any way to get Grub on the flash drive to load the copy of Grub from the HDD in the machine (or load Windows only in the absence of a local Grub install)?

I know I could just as easily reboot and take the thing out of the USB port, but I'll also be working with technicians who have no experience with Linux boot loaders, and I'd like to make it as straightforward as I can.

Any suggestions?  Thanks much!

---

### Post by Fire_Chief on 2009-02-12
I don't have a direct answer for this but maybe a direction to point you in.
The Ubuntu LiveCD and several others give the option when you boot to it to either install, boot to live environment, or boot first hard drive (typically where the MBR sits). You may want to see how they accomplish that last option.

Cheers!

---

### Post by caljohnsmith on 2009-02-12
> **bcgirten said:**
> ...is there any way to get Grub on the flash drive to load the copy of Grub from the HDD in the machine (or load Windows only in the absence of a local Grub install)?

Sure, all it usually takes is to add an entry like:
```
title Hard Disk Drive
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
If you have more than one HDD, you might have to use (hd2) in place of (hd1) in all instances above, but I think you get the idea. Let me know how that goes or if you run into problems.

---

### Post by bcgirten on 2009-02-12
> **caljohnsmith said:**
> Sure, all it usually takes is to add an entry like:
```
title Hard Disk Drive
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
If you have more than one HDD, you might have to use (hd2) in place of (hd1) in all instances above, but I think you get the idea. Let me know how that goes or if you run into problems.

It appears to have worked to an extent.  When the drives are swapped in the map statements, the flash drive becomes hd1, so the code listed above sends grub into a recursive load.  I switched the rootnoverify to hd0 and it loaded great.

Thanks much... I had thought that implementing the map statements like you did would simply make both hd0 and hd1 the same thing.  Honestly, I guess it wouldn't really matter.

Thanks again!

---

