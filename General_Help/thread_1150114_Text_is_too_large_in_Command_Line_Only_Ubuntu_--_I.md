---
title: "Text is too large in Command Line Only Ubuntu -- I can't even see the whole screen"
date: 2009-05-05
forum: General Help
---

### Post by willz06jw on 2009-05-05
Hi,

I am using command-line only Ubuntu on a vintage PC.  After I installed, I suddenly noticed I can't see the whole screen.  The characters are WAY too big.

I am using a nVidia RIVA TNT PCI video card.  I managed to install ssh-server and was able to install the oldest version of the nvidia driver through envyng, but it still didn't fix my problem.

Any idea?  The characters were fine when I was using an older S3 (AKA McFlicker) video card (I reinstalled after I put in the "new" video card to make sure the installer saw my new video card).

Thanks for your help,
Will

---

### Post by dcstar on 2009-05-05
> **willz06jw said:**
> Hi,

I am using command-line only Ubuntu on a vintage PC.  After I installed, I suddenly noticed I can't see the whole screen.  The characters are WAY too big.

I am using a nVidia RIVA TNT PCI video card.  I managed to install ssh-server and was able to install the oldest version of the nvidia driver through envyng, but it still didn't fix my problem.

Any idea?  The characters were fine when I was using an older S3 (AKA McFlicker) video card (I reinstalled after I put in the "new" video card to make sure the installer saw my new video card).

Thanks for your help,
Will

You can use a "vga=" kernel boot option to select different VGA modes.

---

### Post by willz06jw on 2009-05-06
how do I boot with that mode?

Thanks for your help,
Will

---

### Post by CatKiller on 2009-05-06
It's probably worth testing the mode that you want before you put it in GRUB's menu.lst. You get the chance to edit the line you'll boot from from the GRUB menu. Put in vga=<some mode number> at the end of the kernel line. There's a list of mode numbers on [Wikipedia]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers") and elsewhere. The modes that are supported are video card specific, so some might not work for you. Personally, I've not had any success with decimals; hex numbers are the only ones that seem to work for me so I use vga=0x31B for 1280×1024×24 (I think that Wikipedia page mentions the offset between VESA mode number and Linux mode number; for hex values add 200 to the hex values that are in the table above).

Once you've got a mode number setting that you're happy with, you can put it in your GRUB configuration with ```
sudo nano /boot/grub/menu.lst
``` Put it at the end of the kernel lines for your non-recovery Linux menu options, and if you want it to be applied to any future versions as well put it in the defoptions line.

---

### Post by willz06jw on 2009-05-06
Only the vesa 256 color modes work.  Why is that?  The characters on my 386 msdos computer were smaller.

---

### Post by willz06jw on 2009-05-08
There seem to be many people who are using the RIVA TNT card that are having this issue.  The level 3 characters are just way too large.

Recap:  The only way to see all of the characters displayed on the screen is too modify grub to boot in a 256 color VESA mode (vga=261 seems the best for me).  This is still horrible and the letters are larger than what was displayed on a commodore 64.  

There has to be a way to have Ubuntu load the command line level in a normal resolution!

If anyone knows how I will salute you!

Will

---

### Post by CatKiller on 2009-05-08
The modes that are available depend entirely on the card's own implementation of the VESA specification. I believe there is a way to get GRUB to list the modes that are available for your framebuffer device (vga=ask, perhaps?) that might list some numbers that you haven't tried.

I also believe that there are a handful of different framebuffer modules built into the kernel, and that it's possible to choose which modules to load, and that there is a rivafb module that is distinct from the vesafb module. That's about the far limit of my knowledge on the matter. I don't know how to check which modules are available, what support they'd give, or how to enable them. But that might be a different approach you could try.

---

### Post by mcduck on 2009-05-08
> **CatKiller said:**
> The modes that are available depend entirely on the card's own implementation of the VESA specification. I believe there is a way to get GRUB to list the modes that are available for your framebuffer device (vga=ask, perhaps?) that might list some numbers that you haven't tried.

I also believe that there are a handful of different framebuffer modules built into the kernel, and that it's possible to choose which modules to load, and that there is a rivafb module that is distinct from the vesafb module. That's about the far limit of my knowledge on the matter. I don't know how to check which modules are available, what support they'd give, or how to enable them. But that might be a different approach you could try.

yes, adding "vga=ask" to kernel parameters will result in a list of available modes when booting the machine.

---

### Post by willz06jw on 2009-06-02
Most of the available modes don't work correctly -- I still cannot get a reasonable sized font.  I was able to install SSH at least I can work on it from other computers :( (if I figure out what was wrong with the thing).

---

