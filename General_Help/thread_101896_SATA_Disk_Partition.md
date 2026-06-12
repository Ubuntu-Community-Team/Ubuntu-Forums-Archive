---
title: "SATA Disk Partition"
date: 2005-12-10
forum: General Help
---

### Post by Oldan on 2005-12-10
I wanted to mimic my old Gentoo install and I did my disk partition like so:
[LIST]
[*]SDA1 -> Boot Partition mounted at /boot
[*]SDA2 -> Root Partition mounted at /
[*]SDA3 -> Swap
[*]SDA4 -> *** Extended Partition ***
[*]SDA5 -> USR Partition mounted at /usr
[*]SDA6 -> VAR Partition mounted at /var
[*]SDA7 -> HOME Partition mounted at /home
[/LIST]
Unfortunately, during the install of GRUB the darned thing halted about 50% the way through during guessing the Bios disks. When I let Ubuntu repartition into two partitions (gigantic root and swap), it worked fine.

Is this partitioning scheme unworkable in the Ubuntu? It worked fine in Gentoo. And I liked the fact that the Boot partition was unmounted after the boot was done.

--Oldan

---

### Post by soulestream on 2005-12-10
are they all primary partitions?

soule

---

### Post by Oldan on 2005-12-10
[QUOTE=soulestream]are they all primary partitions?[/QUOTE]
Nah...
5 through 7 are extended.
--Oldan

---

### Post by soulestream on 2005-12-10
> SDA4 -> *** Extended Partition ***

guess i should read better. May not be your patitioning scheme that caused the problem. The only other thing i can think of is make sure they are big enough and that they are formatted correctly.

soule

---

### Post by Oldan on 2005-12-11
[QUOTE=soulestream]May not be your patitioning scheme that caused the problem. The only other thing i can think of is make sure they are big enough and that they are formatted correctly.[/QUOTE]

Good point, I had 1gb for boot and 5gb for root (the rest are less critical I would think, but they were 30gb or so each). If there wasn't sufficient space to install the second phase, GRUB might have hung.

Since it is "so easy" to install Ubuntu (now that I'm past the "No Installable Kernel Found" problem), I think I'll try it again.

--Oldan

---

