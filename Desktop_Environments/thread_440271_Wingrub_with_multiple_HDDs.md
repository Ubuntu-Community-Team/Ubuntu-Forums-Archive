---
title: "Wingrub with multiple HDDs"
date: 2007-05-11
forum: Desktop Environments
---

### Post by DemonOne on 2007-05-11
Installing any operating system to the beginning of a drive is impotent.

I initially installed Ubuntu into a partition located after 300GB, which rendered it unbootable since the BIOS was unable to reach it.

Anyway, I repartitioned (new empty drive anyway) and problem solved.


> Hello,

I have two HDDs one on Primary ATA, and the other on Primary SATA.
WinXP is installed and booted from the ATA disk.
I installed Ubuntu on my SATA disk and made GRUB install into the root partition (/dev/sda2).

I tried extracting GRUB with dd and have NTDLR use it, but all I got was a blank screen with the text "GRUB", suppose this happens because Ubuntu is installed on the other HDD.
I then tried to configure Wingrub to boot linux, but get an error message when selecting Ubuntu from the Wingrub menu telling me that the BIOS doesn't support the cylinder whatever thing (can't get to the exact error message right now).

Wingrub's MENU.LST:
timeout 10

title Windows at (hd0,0)
root (hd0,0)
title Ubuntu at (hd1,1)
root (hd1,1)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1


I'd appreciate any kind of help.

Thanks,

Demon.

---

