---
title: "Elementary os installation failure [$15]"
date: 2014-12-12
forum: Debian
---

### Post by andrew178 on 2014-12-12
Hi guys, i've been trying for a few hours now and i still cannot find out why I cannot install elementary os.
Every time i try to install elementary os I get "the 'grub-efi' package failed to install into /target/", I am trying to dual boot elementary with Windows 8.1, I have wiped my ssd and set it as msdos to see if it worked, it did not.

I have now used boot-repair in order to see what is wrong, it says "The boot of your pc is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB-250MB, start of the disk, boot flag). And after a few seconds i get "grub-pc purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].

Bootinfo summary: [http://paste.ubuntu.com/9488247/](http://paste.ubuntu.com/9488247/)

Whoever helps me fix this first will get $15 BTC
I need it fixed ASAP as dualboot with windows 8.1

---

### Post by ajgreeny on 2014-12-12
So have you made the 100MB-250MB fat32 partition it tells you to?

It looks as if there is one from the parted info in the report and that it has the boot flag, which is needed if it is to work, but for some reason Boot-repair is not seeing it according to the final repair comment.

I don't think I can help more, I'm afraid.

---

