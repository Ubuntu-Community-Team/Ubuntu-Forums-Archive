---
title: "Dell Inspiron 7000 ten years old"
date: 2010-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by billmiller on 2010-06-04
Which version of ubunto is appropriate to install on my 10 year old Inspiron 7000 laptop?
Thank you for your help.

---

### Post by efflandt on 2010-06-05
What CPU and video chip does it have, or more importantly how much RAM does it have.

If its BIOS is from 1999 or earlier, you may need to use **acpi=force** kernel parameter to use acpi.  On an old Pentium III 550 MHz desktop I also had to use **lapic** parameter (although, that was a Gateway that I rounded up 512 MB PC100 RAM for).

Linux itself has been around for a long time.  The first computer I used it on was a 386DX33 with added 387 math co-processor, later hot rodded to 486DRx2/66.  I had to add a card to use more than 528 MB of a 540 MB drive (in order to do LBA translation).

---

### Post by BoneKracker on 2010-06-05
Bottom Line: I'd try Lubuntu, but don't listen to me because I'm not even an Ubuntu user. :)

Pentium II or Celeron
266 - 400 MHz
440BX AGP chipset
Maximum of 384 MiB RAM
[http://support.dell.com/support/edocs/systems/pcyc/specs.htm](http://support.dell.com/support/edocs/systems/pcyc/specs.htm)

I've run Xfce4 and a light linux setup on a similar machine before.  So, you might be able to run Ubuntu Miminal.  I think I'd go lighter, though.  I might try Lubuntu on that, although I personally have no experience with LXDE.

You can probably make it run with whatever RAM you've got, but you probably need at least 256 MiB or so to be productive. With that much or less RAM, you'll get bogged down running something like Firefox or OpenOffice (and it will be swapping for sure if you run both at the same time).  You would want to seek the lighter alternatives (which may already be the defaults in things like Lubuntu).

I don't know what Lubuntu uses for an installer, but if it uses a LiveCD or a graphical installer, you may have trouble with that (if you have limited RAM).  If you think that will be the case, there may be a text-based or "alternate" install CD.

The good news is it's got a good chipset that is well-supported in the Linux ecosystem.  You should also have no problem using your sound and video acceleration hardware.  That website didn't provide much information on the touchpad -- you might want to have a mouse handy.

---

### Post by ugm6hr on 2010-06-05
If you are a Linux beginner, I'd consider non-Ubuntu options...

Ubuntu will work well from a Minimal install base - see the linke Ubuntu + LXDE below.

However, it would be simpler to use a distro specifically designed for low end systems - Antix and Puppy Linux are good options.

---

### Post by waynefoutz on 2010-06-05
> **ugm6hr said:**
> If you are a Linux beginner, I'd consider non-Ubuntu options...

Ubuntu will work well from a Minimal install base - see the linke Ubuntu + LXDE below.

However, it would be simpler to use a distro specifically designed for low end systems - Antix and Puppy Linux are good options.

Puppy Linux would run pretty good on that machine, I can tell you that from experience.  Lubuntu looks promising, but I've never tried that one. It's been a while since I had a machine that old in my possession.

---

### Post by Joe of loath on 2010-06-08
I've got a similar spec machine built into my stereo system that I play music on, it runs puppy great.

---

