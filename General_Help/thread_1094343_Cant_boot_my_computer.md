---
title: "Cant boot my computer"
date: 2009-03-12
forum: General Help
---

### Post by limiz on 2009-03-12
Starting up:
    1.376116] Kernel panic - not syncing: VFS : Unable to mount root fs on a unknown - block (0,0)

That what it give me when starting up my computer. I just install kubuntu 8.10. 
What I remember doing. I was updating. And it ask me for what hardware to install. I went for what was recemented  for my computer. It was something like 707. Right now I'm using kubuntu 8.10 live cd. So how would I fix this start up computer problem? I'm still a noobie at linux. But I'm starting to get the hang of thing.

---

### Post by kmac on 2009-03-12
What text is before the Kernel Panic?

This will determine what the computer was doing when it ran into a problem.

---

### Post by Zorael on 2009-03-12
Well, this could be because your /etc/fstab or /boot/grub/menu.lst link wrong to the root partition.

Usually, drives and partitions are referenced towards by their device node, like /dev/sda (drive) and /dev/sda1 (partition). However, if you have a harddrive rack and you frequently remove/add disks, what was /dev/sdb could suddenly be /dev/sdc, and all hell would break loose. Hence, fstab references toward partitions using their unique-ish UUIDs that don't change if you change driver order. GRUB uses a mix of the two, as well as another partition enumeration system; (hd0,0) is the first partition for the first drive, (hd1,2) is the third partition for the second drive, etc.

From your live cd, you can run **blkid** in a terminal to make it list your UUIDs. Figure out which belongs to your root partition and compare entries in /etc/fstab in your installed root partition (not the live cd's, obviousy) as well as in /boot/grub/menu.lst.

Some examples.

blkid:
```
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="RECOVERY" UUID="A05E-0310" TYPE="vfat"
/dev/sda2: UUID="02F840B6F840A9AD" LABEL="XP" TYPE="ntfs"
/dev/sda3: UUID="ac62aa1d-d789-4a52-917b-6c1ec082b10b" TYPE="swap"
/dev/sda4: UUID="[COLOR="RoyalBlue"]d87928e1-b48e-407e-b190-c12d861019d8[/COLOR]" TYPE="ext4"
```

Relevant piece of /etc/fstab; my root is [COLOR="RoyalBlue"]d87928e1-b48e-407e-b190-c12d861019d8[/COLOR] which was /dev/sda4 at installation:
```
# <file system>					<mount point>	<type>	<options> <dump> <pass>
proc            				/proc           proc    defaults 0 0
# / was on /dev/sda4 during installation
UUID=[COLOR="RoyalBlue"]d87928e1-b48e-407e-b190-c12d861019d8[/COLOR]	**_/_**               ext4    noatime,errors=remount-ro 0 1
```

Relevant kernel entry in /boot/grub/menu.lst:
```
title           Kubuntu 9.04a5: Jaunty Jackalope (2.6.28-9)
uuid            [COLOR="RoyalBlue"]d87928e1-b48e-407e-b190-c12d861019d8[/COLOR]
kernel          /boot/vmlinuz-2.6.28-9-generic root=UUID=[COLOR="RoyalBlue"]d87928e1-b48e-407e-b190-c12d861019d8[/COLOR] ro splash vga=6 quiet
initrd          /boot/initrd.img-2.6.28-9-generic
quiet
savedefault
```

Examples were taken from a Jaunty installation, so stuff may differ from yours. Consider reading [the Ubuntu wiki entry on fstab](https://help.ubuntu.com/community/Fstab) for more information.

---

### Post by limiz on 2009-03-12
> **kmac said:**
> What text is before the Kernel Panic?

This will determine what the computer was doing when it ran into a problem.

Boot from (hd0,0) ext3  9ac52340 - f02f - 4e1c - 8f44 - 95314219e6(or b)39

---

