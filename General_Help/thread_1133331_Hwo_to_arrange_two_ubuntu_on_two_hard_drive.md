---
title: "Hwo to arrange two ubuntu on two hard drive"
date: 2009-04-22
forum: General Help
---

### Post by helai on 2009-04-22
Hello,

I want to keep my hardy when I try the new OS Jaunty.so I want to arrange my ubuntu like following

Hardy 8.04 with EXT3 installed in hda ( one hard drive),it's grub installed in hda
Jaunty 9.04 with EXT4 installed in sda (one hard drive),it's grub installed in sda

Now I am wondering where the grub of hardy can boot the Jaunty,if so ,whether it will influnce the speed of the EXT4,because I worry the grub of hardy is not updated for EXT4.

Is it possible that hardy can recognize the EXT4 partition? Because the kernel of the hardy can't support the EXT4

How can I arrange these two OS ?

Thanks
Helai

---

### Post by DagMan on 2009-04-23
You'de have to use Jauty's grub to boot, but when you install jaunty it will likely detect hardy and handle booting of it, adding it to the grub entry.  If it isn't going to be a permanent setup then you'lle want to know how to restore hardy's grub removing jaunty.  There's threads explaining how to do so.

Hardy won't be able to read the ext4 filesystem.  There may be a patch for the kernel hardy uses, then you'de have to recompile the kernel and if you're using any restricted modules, backport modules, video card drivers from the repos, etc, then you'de need to think about that too as they'd have to be redone.  I'd sooner try using the jaunty kernel source and compile it within hardy than bother with all the patching.

---

