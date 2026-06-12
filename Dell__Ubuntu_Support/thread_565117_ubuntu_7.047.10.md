---
title: "ubuntu 7.04/7.10"
date: 2007-10-01
forum: Dell  Ubuntu Support
---

### Post by sidyom on 2007-10-01
well, i had originally had ubuntu 6.06 a while ago obviously, and i decided to leave it because my wireless USB dongle had no support for it.
well, i recently wanted to get back into ubuntu, so i downloaded the newest stable, 7.04. i made the cd, checked it, etc.
but when i put the cd in my drive to boot from it, on 7.04 it was saying "kernel panic: VFS: unable to mount root fs on unknown block (104,1)"

so i decided to go with a newer version, even though it was the beta.

but now when i start my computer with the cd in the drive, it just hangs with a blinking underscore.

any help/suggestions will be appreciated.

---

### Post by pondochris on 2007-10-02
Don't know if this will help but when I try to boot up puppy or dsl live cd's I have to set the boot parameter ACPI=off otherwise it will hang on startup. Also do you have enough ram to run the live CD? If not you may want to try the text based installer.

---

### Post by sidyom on 2007-10-02
1 GB DDR?
i think i do. :)

but i try it with the acpi=off at boot, and still i get the error of
kernel panic: vfs: unable to mount......at block (104,1)

sys specs:
dell b110
80GB hdd (stock)
intel 82865G graphics controller (stock)
mitsumi CR-4804TE (drive i'm booting cd from)
intel celeron D - 2.53 GHz

---

