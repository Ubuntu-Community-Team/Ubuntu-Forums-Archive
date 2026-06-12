---
title: "kernel hang.....please help!"
date: 2006-07-20
forum: Desktop Environments
---

### Post by noday42 on 2006-07-20
I really need some help!

Ubuntu was booting fine yesterday, and the days before that. But today, when I went to boot, the system hanged at "Uncompressing Linux kernel"

I did update the kernel yesterday to 2.6.15-26-386 I believe, but even when I use the grub menu to go back to an older kernel, I get kernel panics (Attemped to kill the idle task!) or hanging at "Mount-cache hash table entries: 512)

I've tried googling and searching the forums....I tried turning acpi off, but I didn't do anything. I was able to boot once into one of the older kernels, then subsequently once into the new kernel, but after I rebooted again, back to the kernel hang......any help would be appreciated!

---

### Post by philippe_carlo on 2006-07-20
This sounds really strange. The sudden appearance of the issue and the inconsistent behavior (i.e., booting once, next time not booting) makes me think in the direction of hardware problems. Can you boot with the live CD? How about running some memory tests?

---

### Post by noday42 on 2006-07-20
if the live cd is the same as the install cd....then I can get the cd menu, but can't actually boot into Ubuntu

ran a memtest for 7+ hours and it still wasn't done...tried rebooting again....and nothing. i did try to look at the error reports before i rebooted and did see quite a few errors....could it be a problem with the memory?

now that i think about it, towards the ends of this computer's XP days, it was having LOTS of trouble booting up, and random stop errors and BSOD. I'll try each memory stick individually and see if that changes anything

anyone have any other ideas?

---

### Post by noday42 on 2006-07-21
nevermind....looks like all those errors were pointing to something....a bad stick of memory. Good thing Mythtv still runs awesome on 256 MB of RAM instead of 712!

---

