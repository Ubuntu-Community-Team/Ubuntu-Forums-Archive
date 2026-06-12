---
title: "'noacpi' append to kernel line.."
date: 2005-06-25
forum: Desktop Environments
---

### Post by neighborlee on 2005-06-25
just wondering if anyone has found that using 'noacp' on kenrnel line fixes  X crashing bug so many have seen??..want to verify before I go to bother of reinstalling is all..this is sad I sure miss ubuntu! but I can't be crashing all the time ( and I desperately need 3d drivers)

thx
neighborlee

---

### Post by Xian on 2005-06-25
I certainly have seen this work on systems before, but of course it would not be possible to predict with certainty that it will resolve your issue as there are a myriad of reasons why X sometimes freezes.

For example, I had X freezes all the time with Debian's Sarge (both testing and eventual release stages), and tried about every conceivable grub parameter, video driver, kernel, and even switched to Xorg on one occasion. But none of it helped and I kept getting freezes. I eventually discovered it had to do with the sound server, and after changing to alsa everything cleared up fine.

When it comes to X configs and freezes there can be alot of grey area.

---

### Post by astoltz on 2005-06-25
It did not work on my system with an nVidia graphics card.  I can still use the nVidia drivers but I have to set RenderAccel = "off".  No crashes with that config.

---

### Post by neighborlee on 2005-06-25
[QUOTE=astoltz]It did not work on my system with an nVidia graphics card.  I can still use the nVidia drivers but I have to set RenderAccel = "off".  No crashes with that config.[/QUOTE]

hmm..so you still use nvidia drivers but renderaccel is set to off ?..I have never used such options in my xorg.conf but I presume that makes toast of games or apps that utilize such functions ...?

thx
nl

---

### Post by alastair on 2005-06-25
You should read the NVidia README - it should be somewhere e.g. under /usr/share/doc somewhere. The option you mention might still be marked "experimental" - check the docs.

As for ACPI - do you mean "acpi=off" on the kernel line?

---

### Post by doans on 2005-06-25
I have a Nvidia card and tried the noacpi line and it did not help the random crashing at all. In fact the only thing that seems to stop the random lockups for me is to disable any advanced features in BIOS. Now, I can actually enjoy Ubuntu and not try and diagnose the latest lockup.

But, I have seen posts that the noacpi line seems to work for some and not for others. I just had to expriment with them all until I found a working solution.

---

