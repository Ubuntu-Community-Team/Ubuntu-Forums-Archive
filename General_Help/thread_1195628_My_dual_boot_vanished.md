---
title: "My dual boot vanished?"
date: 2009-06-24
forum: General Help
---

### Post by Nubi505 on 2009-06-24
I installed Linux Mint with win4mint for testing purposes and then installed Ubuntu with Wubi once I figured out what I wanted to do. I noticed Linux Mint vanished from the boot list and was replaced with Ubuntu, which was fine because I didn't really want Mint, I wanted Ubuntu. I just uninstalled Linux Mint and now there are no boot choices. It just goes straight into Windows XP (my original OS) and doesn't give me a choice to boot into Ubuntu. 

Ubuntu is still installed, so where did my dual boot screen go? Is there a way to fix this or boot into Ubuntu without a reinstall? 

Thanks

---

### Post by Abraxis on 2009-06-24
A quick and temporary fix would be to use knoppix live cd, or Ubuntu live cd (should be an option on the ubuntu install cd 'try ubuntu without any changes to my computer').  Go into terminal
[I]
sudo fdisk /dev/sda[/I]
*p*

Find the partition ubuntu boots from (should be the smallest linux filesystem)

then make that the partition you boot from instead of the windows.

[I]a 
(number of windows partition)[/I]
[I]a 
(number of linux boot partition)[/I]

*w* (to write to disk)

restart and you'll get into linux

---

### Post by Nubi505 on 2009-06-24
I installed Ubuntu using Wubi, so it doesn't have its own separate partition (I tried a million different ways, I can't create new partitions). 

I also want to be able to boot into Windows at any time. 

So do your instructions still apply? I'm new to Linux and command lines/the terminal.

---

