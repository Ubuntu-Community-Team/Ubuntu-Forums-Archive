---
title: "Help with explanation"
date: 2006-08-28
forum: Desktop Environments
---

### Post by PaulFXH on 2006-08-28
This problem is resolved but I cannot fully understand exactly why. Perhaps somebody can help me with an explanation.
Here's the situation:

I use a multiboot system with WinXP and five Linux distros (two of which are on a "non-bootable" usb hd). I normally boot from the internal hd which brings up a boot option menu showing WinXP and three distors (plus recovery modes).
In addition, I can use a bootcd to show an extended boot option menu with the same as before as well as the two distros on usb hd.

Last week, I messed up Grub in the mbr so that booting from the internal hd launched exclusively WinXP---no boot option menu appeared.
However, booting from the cd functioned as it always has done with the full menu displayed.

Is there really enough room on that tiny little grub file in the mbr to permit, for example, Ubuntu booting from the cd but preventing it from the hd?
Or is there some other explanation?

BTW, I restored the boot option menu (from the internal hd) by re-installing Grub in the mbr from the Ubuntu Dapper install disk in rescue mode.

---

### Post by bullgr on 2006-08-28
win xp and five linux distros?
did you want to play sudoku with grub? :biggrin: 
this is realy painfull, you get confused and last, you get all messed up.

use only dual boot (perhaps win xp and linux) or at least triple boot (with the third distro installed its own grub in the distro partition) but not that what you make... you always get problems with this...

---

### Post by PaulFXH on 2006-08-28
Well, thanks for worrying for me, but I assure you it is quite unnecessary. I used this multi-boot system for a few weeks with NO problems and MANY advantages for what I'm trying to do.
I haven't mentioned what caused my Grub problem but it was nothing to do with me having 5 distros.
Now that I've cleared that up, any ideas about my original question?

---

