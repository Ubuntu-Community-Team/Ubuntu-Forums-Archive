---
title: "Trying to install ubuntu on macbook"
date: 2009-03-15
forum: General Help
---

### Post by .gurkburk on 2009-03-15
I cant get ubuntu installed on my macbook, ive been trying this weekend, but no luck.

Im 100% sure the problem itself is the lack of a normal bios on the macbook, and its the "efi" system causing thing.

Right now I have installed ubuntu 9.04 alpha 6 (also been trying with 8.10..) and the installation runs well, but when I boot, the macbook cant find anything to boot from.

If I insert a ubuntu installation cd and choose "boot from first harddrive" it works fine, and same thing with running a cd called "refit" and choosing "boot from linux on harddrive", it runs up smoothly, thus, the problem is in the bootloader itself.

I have used the utility in gparted to remake the partition table to msdos instead of the apple-default, whichever that is, that comes with the laptop, so its the "right" stuff.

Ive tried to reinstall over the entire drive, or try to keep the 200mb "efi" labeled partition, no difference at all.

Im actually not sure what todo, most instructions, guides, tutorials and documentation I can find simply states "just install refit and everything works", which is /fail in this case.

Any ideas?

Edit: its the new macbook unibody that runs intel core 2 duo CPUs.

---

### Post by perrti-y02 on 2009-03-15
If you boot into the live cd and open up Gparted can you change the bootable flag to be on the partition with GRUB on it? (this is probably going to be the same as the ubuntu drive)

Do this by right clicking on the partition and then go down to Manage Flags. there should be an option  Boot  with a tickbox.

---

### Post by .gurkburk on 2009-03-15
> **perrti-y02 said:**
> If you boot into the live cd and open up Gparted can you change the bootable flag to be on the partition with GRUB on it? (this is probably going to be the same as the ubuntu drive)

Do this by right clicking on the partition and then go down to Manage Flags. there should be an option  Boot  with a tickbox.

Changing this back and forth makes no difference at all, I have already tried it (the partition I  choose to mount root on, and the "efi" one that existed when I started).

Im gonna try to install it through bootcamp in macOSx instead, since that seems to make it easier.. I just dont like the idea of having a slacking macOS on the laptop, for the only purpose of being able to actually boot ubuntu...

---

