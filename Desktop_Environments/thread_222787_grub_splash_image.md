---
title: "grub splash image"
date: 2006-07-25
forum: Desktop Environments
---

### Post by fred_slayer on 2006-07-25
i sucessufully changed the splash image for my GRUB, but the "box" where the operational system to be loaded is selected is too big!!! and because of that i can only see a small piece of the splash image.

so, is there a way to make that "box" transparent???
or, can i make that box smaller??

ty.

---

### Post by Irony on 2006-07-25
I haven't tried this but I think if you go to the section in your menu.lst;

[PHP]## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all[/PHP]

and change it to say;

[PHP]## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1[/PHP]

Then it will make the Grub box smaller.

---

### Post by fred_slayer on 2006-07-25
no, it didn't worked... the box remains big.

---

