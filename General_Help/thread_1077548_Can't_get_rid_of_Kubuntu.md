---
title: "Can't get rid of Kubuntu"
date: 2009-02-22
forum: General Help
---

### Post by Flanger on 2009-02-22
Hello everybody, Its my first post here, hope I've opened it in appropriate section.

The problem is:

I've got HP/Compaq 6720s Notebook with preinstalled kubuntu but I really need to have Windows XP installed on it. As you probably can guess already, my windows XP SP2 installation setup can't detect hard drive, I know its a known problem and I've seen several threads regarding it here but my problem is a bit different. I need to completely get rid of ubuntu and have clean WXP installation.

Here are the steps I've tried:

Got GParted live and booted into it.
Deleted whole partitioning table.
Made new partitioning table (msdos, default).

And then any combinations I could. I left it unallocated, setup cant see. Formatted with NTFS - same, formatted with FAT - same.
Also tried out flagging it as bootable, same problem.

I've also found on google several threads regarding AHCI configuration, that windows couldn't detect HDD because of that setting in BIOS, but this notebook doesn't have AHCI / ATA Switch in BIOS, its working as SATA Native, besides I've reinstalled windows on other 6720s machines (two of them) without a problems.

I still think its partitioning on MBR problem, don't know how to fix, all I have is bootable GParted, and I think it doesnt actually format my HDD, as when I order format operation and apply it takes GParted a couple of seconds to finish the process...

P.S. Excuse me if I haven't provided enough information, I'm almost newbie in nix systems.

---

